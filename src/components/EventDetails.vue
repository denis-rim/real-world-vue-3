<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>Event #{{ $route.params.id }}</p>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from '@/services/EventService'
export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    // fetch event (by id) and set local event data
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  },
}
</script>

<style scoped></style>
