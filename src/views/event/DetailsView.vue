<template>
  <h1>{{ event.title }}</h1>
  <p>Event #{{ $route.params.id }}</p>
  <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
  <p>{{ event.description }}</p>
</template>

<script>
export default {
  props: ['event'],
}
</script>

<style scoped></style>
