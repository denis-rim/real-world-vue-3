<template>
  <h1>Register for the event</h1>
  <button @click="register">Register Me</button>
</template>

<script>
export default {
  props: ['event'],
  methods: {
    register() {
      console.log('Registering for the event')
      this.$router.push({ name: 'EventDetails' })
    },
  },
}
</script>

<style scoped></style>
