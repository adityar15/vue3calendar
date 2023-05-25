<template>
  <div class="max-w-2xl mx-auto py-16">
    <!-- <Calendar class="w-full" /> -->
    <!-- <TagInput /> -->
    <!-- <ProgressBar :progress="progress" /> -->
    <NameSelector />
  </div>
</template>

<script setup lang="ts">
import {defineAsyncComponent, onMounted, ref} from 'vue'

// const Calendar = defineAsyncComponent(() => import('./components/calendar/index.vue'))
// const TagInput = defineAsyncComponent(() => import('./components/tag/TagInput.vue'))
// const OTPPad = defineAsyncComponent(() => import('./components/pin/OTPPad.vue'))
// const ProgressBar = defineAsyncComponent(() => import('./components/progress/ProgressBar.vue'))

const NameSelector = defineAsyncComponent(() => import('./components/refactored/NameSelector.vue'))



</script>

