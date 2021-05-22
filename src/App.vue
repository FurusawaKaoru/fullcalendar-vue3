<template>
  <FullCalendar :options="calendarOptions" />
</template>

<script lang="ts">
import '@fullcalendar/core/vdom'
import dayGridPlugin from '@fullcalendar/daygrid'
import interactionPlugin from '@fullcalendar/interaction'
import { defineComponent } from 'vue'
import FullCalendar from '~/components/FullCalendar.vue'

export default defineComponent({
  name: 'App',
  components: {
    FullCalendar
  },
  setup() {
    const calendarOptions = {
      plugins: [ dayGridPlugin, interactionPlugin ],
      initialView: 'dayGridMonth'
    }
    return {
      calendarOptions
    }
  }
})
</script>

<style>
</style>
