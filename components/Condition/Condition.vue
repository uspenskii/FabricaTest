<template lang='pug'>
form.condition(@change="handle" :style="{ 'background-color': item.color }")
  .condition__next(v-if="index != 0") 
    .condition__and(:style="{ 'background-color': item.color }") И
  .condition__header
    .condition__left 
      h2.condition__title(:style="{ 'color': item.color }") Условие {{ index + 1 }}
    .condition__right
      .condition__select
        select(v-model="form.condition.type")
          option(value="age") Возраст респондента
          option(value="type") Тип
          option(value="status") Статус
  .condition__body
    .condition__range(v-if="item.type == 0")
      .condition__item(v-for="(option, index) in form.range", :key="index")
        .condition__left 
          .condition__or(v-if="index + 1 > 1" :style="{ 'background-color': item.color }") ИЛИ
          p.condition__text(:class="{ and: index + 1 > 1 }") Диапазон {{ index + 1 }}
        .condition__right
          .condition__inputs 
            span от
            input.condition__input(type="text", v-model="option[0]")
            span до
            input.condition__input(type="text", v-model="option[1]")
    .condition__type(v-if="item.type == 1")
      .condition__item(v-for="(item, index) in select", :key="index")
        .condition__left 
          p.condition__text Тип {{ index + 1 }}
        .condition__right
          select.condition__select.type(v-model="form.selected[index]")
            option(
              v-for="option in select[index].options",
              :key="item.id",
              :value="option.value"
            ) {{ option.name }}
  .condition__footer
    .condition__left
    .condition__right
      button.condition__add(
        @click="addRange",
        type="button",
        v-if="item.type == 0"
      ) Добавить диапазон
      button.condition__add(
        @click="addOption",
        type="button",
        v-if="item.type == 1"
      ) Добавить тип
      button.condition__add(
        @click="addOption",
        type="button",
        v-if="item.type == 2"
      ) Добавить статус
      button.condition__delete(@click="remove", type="button") Удалить условие
</template>

<script>
export default {
  props: ["item", "index"],
  data() {
    return {
      name: "",
      select: [
        {
          options: [
            {
              value: "gold",
              name: "Gold",
            },
            {
              value: "silver",
              name: "Silver",
            },
          ],
        },
      ],
      form: this.item.form,
    };
  },
  methods: {
    handle() {
      this.$emit("change", this.form);
    },
    remove() {
      this.$emit("remove");
    },
    addRange() {
      this.form.range.push(["", ""]);
    },
    addOption() {
      this.form.selected.push(null);
      this.select.push({
        options: [
          {
            value: "gold",
            name: "Gold",
          },
          {
            value: "silver",
            name: "Silver",
          },
        ],
      });
    },
  },
};
</script>


<style lang="scss" src='./condition.scss'>
</style>