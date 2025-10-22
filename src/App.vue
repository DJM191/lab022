<script setup lang="ts">
import EventCard from './components/EventCard.vue'
import EventDetails from './components/EventDetails.vue'
import StudentView from './StudentView.vue'
import type { Event } from './types'
import { ref } from 'vue'

// 模拟活动数据
const events = ref<Event[]>([
  {
    id: 5928101,
    category: 'animal welfare',
    title: 'Cat Adoption Day',
    description: 'Find your new feline friend at this event.',
    location: 'Meow Town',
    date: 'January 28, 2022',
    time: '12:00',
    petsAllowed: true,
    organizer: 'Kat Laydee'
  },
  {
    id: 4582797,
    category: 'food',
    title: 'Community Gardening',
    description: 'Join us as we tend to the community edible plants.',
    location: 'Flora City',
    date: 'March 14, 2022',
    time: '10:00',
    petsAllowed: true,
    organizer: 'Fern Pollin'
  }
])

// 简单的页面切换
const currentView = ref('events')

function showEvents() {
  currentView.value = 'events'
}

function showStudents() {
  currentView.value = 'students'
}
</script>

<template>
  <div id="layout">
    <header>
      <div class="wrapper">
        <nav>
          <a href="#" @click="showEvents">Events</a> |
          <a href="#" @click="showStudents">Students</a>
        </nav>
      </div>
    </header>

    <main>
      <div v-if="currentView === 'events'">
        <h1>Events For Good</h1>
        <div class="events">
          <div v-for="event in events" :key="event.id" class="event-container">
            <EventCard :event="event" />
            <EventDetails :event="event" />
          </div>
        </div>
      </div>

      <div v-if="currentView === 'students'">
        <StudentView />
      </div>
    </main>
  </div>
</template>

<style>
#layout {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  padding: 30px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  margin: 0 10px;
  cursor: pointer;
}
nav a:hover {
  color: #42b983;
}
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.event-container {
  margin-bottom: 25px;
}
h1 {
  margin: 20px 0;
}
h2 {
  font-size: 20px;
}
</style>