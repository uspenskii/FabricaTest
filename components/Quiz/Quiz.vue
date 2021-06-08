<template lang='pug'>
.quiz
  .quiz__tabs
    .quiz__tab(
      @click="toggleTab(0)",
      :class="{ 'is-active': activeTab === 0 }"
    ) Параметры
    .quiz__tab(
      @click="toggleTab(1)",
      :class="{ 'is-active': activeTab === 1 }"
    ) Вопросы
    .quiz__tab(
      @click="toggleTab(2)",
      :class="{ 'is-active': activeTab === 2 }"
    ) Логика
    .quiz__tab(
      @click="toggleTab(3)",
      :class="{ 'is-active': activeTab === 3 }"
    ) Условия
    .quiz__tab(
      @click="toggleTab(4)",
      :class="{ 'is-active': activeTab === 4 }"
    ) Респонденты
  .quiz__content(v-if="activeTab === 0")
    h2 параметры
  .quiz__content(v-if="activeTab === 1")
    h2 вопросы
  .quiz__content(v-if="activeTab === 2")
    h2 логика
  .quiz__content(v-if="activeTab === 3")
    h2 условия
  .quiz__content(v-if="activeTab === 4")
    h2.quiz__header Добавить вопрос
    .quiz__list
      .quiz__item(v-for="(item, index) in conditions", :key="index")
        Condition(
          :item="item",
          :index="index",
          @remove="removeCondition(index)",
          v-model="conditions[index]"
        )
    .quiz__add-condition
      .quiz__condition-options
        .quiz__left 
          h2.quiz__title Условие
        .quiz__right
          select(v-model="type")
            option(value="0") Возраст респондента
            option(value="1") Тип
      .quiz__field 
        .quiz__add(@click="addCondition") Нажите чтобы добавить новое условие выборки. <br> Все условия связываются между собой логическим "И"
    .quiz__footer
      button.quiz__test Протестировать опрос
      button.quiz__next(@click="send") Далее
</template>



<script>
import axios from "axios";

export default {
  props: ["data", "headline"],
  data() {
    return {
      conditions: [],
      selected: [1, 2, 3],
      activeTab: 4,
      type: 0,
    };
  },
  methods: {
    send() {
      axios
        .post("/sendform", {
          form: this.conditions,
        })
        .then((data) => {
          console.log(data);
        })
        .catch((err) => {
          console.error(err);
        });
    },
    addCondition() {
      const randomColor = Math.floor(Math.random() * 16777215).toString(16);
      let color = "#" + randomColor + "4f"    

      this.conditions.push({
        color,
        type: this.type,
        form: {
          condition: {
            type: "",
          },
          selected: [],
          range: [],
        },
      });
    },
    removeCondition(index) {
      this.conditions.splice(index, 1);
    },
    toggleTab(index) {
      this.activeTab = index;
    },
  },
};
</script>

<style lang='scss' src='./quiz.scss'></style>