<template lang='pug'>
.page__content
  .container
    Header
    Breadcrumb(:data='breadcrumbs')
    p Заглушка для страницы Информации
</template>

<script>
export default {
  layout: 'default', 
  data() {
    return {
      breadcrumbs: [
        {
          title: 'Инфо',
        },
      ]
    }
  },    
}
</script>