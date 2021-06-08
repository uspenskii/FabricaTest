<template lang='pug'>
.header
  .header__search
    input(type='search' placeholder="Поиск по системе")
  .header__user
    img(src='/person.png').header__person
    .header__container
      .header__name Alex
      .header__position Admin
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          link: '/interviews',
          image: '/file.svg',
          text: 'Опросы',
        },
        {
          link: '/users',
          image: '/users.svg',
          text: 'Пользователи',
        },
        {
          link: '/black-lists',
          image: '/flag.svg',
          text: 'Черные списки',
        },
        {
          link: '/call-center',
          image: '/phone.svg',
          text: 'Колл-центр',
        },
      ]
    }
  },
};
</script>

<style lang='scss' src='./header.scss'></style>