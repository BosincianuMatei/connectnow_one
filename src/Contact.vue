<template>
  <HeaderContact />
  <ContactContent />
</template>

<script>


import HeaderContact from './components/HeaderContact.vue'
import ContactContent from './components/ContactContent.vue'

export default {
  name: 'ContactPage',
  components: {
    HeaderContact,
    ContactContent
  },
}

</script>
