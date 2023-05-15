<template>
  <div class="max-w-2xl mx-auto py-16">
    <!-- <Calendar class="w-full" /> -->
    <!-- <TagInput /> -->
    <ProgressBar :progress="progress" />
  </div>
</template>

<script setup lang="ts">
import {defineAsyncComponent, onMounted, ref} from 'vue'

// const Calendar = defineAsyncComponent(() => import('./components/calendar/index.vue'))
// const TagInput = defineAsyncComponent(() => import('./components/tag/TagInput.vue'))
// const OTPPad = defineAsyncComponent(() => import('./components/pin/OTPPad.vue'))
const ProgressBar = defineAsyncComponent(() => import('./components/progress/ProgressBar.vue'))

const progress = ref(0)

onMounted(() => {

  let interval = setInterval(()=>{
    progress.value += 5
    if(progress.value >= 100){
      clearInterval(interval)
    }
  }, 1000)
})

</script>

