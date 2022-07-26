<template>
  <h1>Register for the event</h1>
  <button @click="register">Register Me</button>
</template>

<script>
export default {
  props: ['event'],
  inject: ['GStore'],
  methods: {
    register() {
      console.log('Registering for the event')
      this.GStore.flashMessage = 'You are successfully event' + this.event.title

      setTimeout(() => {
        this.GStore.flashMessage = ''
      }, 3000)

      this.$router.push({ name: 'EventDetails' })
    },
  },
}
</script>

<style scoped></style>
