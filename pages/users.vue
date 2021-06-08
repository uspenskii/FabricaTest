<template lang='pug'>
.page__content
  .container
    Header
    Breadcrumb(:data='breadcrumbs')  
    p Заглушка для страницы Пользователи
</template>

<script>
export default {
  layout: 'default',
  data() {
    return {
      breadcrumbs: [
        {
          title: 'Пользователи',
        },
      ]
    }
  },  
}
</script>