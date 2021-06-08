<template lang='pug'>
.page__content
  .container
    Header
    Breadcrumb(:data='breadcrumbs')
    Quiz
</template>

<script>
export default {
  layout: "default",
  data() {
    return {
      breadcrumbs: [
        {
          title: 'Опросы',
        },
      ]
    }
  },
};
</script>