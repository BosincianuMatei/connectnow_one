<template>
  <HeaderContent />
  <PageContent />
</template>

<script>


import HeaderContent from './components/HeaderContent.vue'
import PageContent from './components/PageContent.vue'

export default {
  name: 'HomePage',
  components: {
    HeaderContent,
    PageContent
  },
}

</script>
