<script setup lang="ts">
import type { Event } from '../types'

defineProps<{
  event: Event
}>()

defineOptions({
  name: 'EventDetails'
})
</script>

<template>
  <div class="event-details">
    <p>{{ event.category }}</p>
    <p>Organized by: {{ event.organizer }}</p>
  </div>
</template>

<style scoped>
.event-details {
  text-align: right;
  font-size: 14px;
}
.event-details p {
  margin: 5px 0;
}
</style>