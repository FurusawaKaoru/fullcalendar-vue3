<script lang="ts">
import { Calendar, CalendarOptions } from '@fullcalendar/core'
import {
  defineComponent,
  h,
  onMounted,
  onUnmounted,
  ref,
  watchEffect,
} from 'vue'

export default defineComponent({
  props: {
    options: Object as () => CalendarOptions,
  },
  setup(props) {
    const el = ref<HTMLElement>()
    const calendar = ref<Calendar>()

    onMounted(() => {
      calendar.value = new Calendar(el.value!, props.options)
      calendar.value.render()
    })
    watchEffect(() => {
      if (calendar.value) {
        calendar.value.pauseRendering()
        calendar.value.resetOptions(props.options)
        calendar.value.resumeRendering()
      }
    })
    onUnmounted(() => {
      calendar.value?.destroy()
    })

    return () => h("div", { ref: el })
  },
})
</script>
