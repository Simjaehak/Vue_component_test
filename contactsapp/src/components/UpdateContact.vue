<template>
  <contactForm mode="update" :contact="contact"></contactForm>
</template>

<script>
  import ContactForm from './ContactForm';

  export default {
    name      : "updateContact",
    components: {ContactForm},
    props     : ['contact']
  }
</script>

<style scoped>

</style>
