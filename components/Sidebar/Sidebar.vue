<template lang='pug'>
.sidebar  
  nuxt-link.sidebar__item(:to='item.link' v-for="item in items" :key="item.id")
    img.sidebar__icon(:src='item.image')
    span.sidebar__name {{item.text}}
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
        {
          link: '/info',
          image: '/question.svg',
          text: 'Информация',
        },
      ]
    }
  },
};
</script>

<style lang='scss' src='./sidebar.scss'></style>