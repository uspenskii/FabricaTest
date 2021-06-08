<template lang='pug'>
.page__content
  .container
    Header
    Breadcrumb(:data='breadcrumbs')
    p Заглушка для страницы Колл-центр
</template>

<script>
export default {
  layout: 'default', 
  data() {
    return {
      breadcrumbs: [
        {
          title: 'Колл-центр',
        },
      ]
    }
  },    
}
</script>