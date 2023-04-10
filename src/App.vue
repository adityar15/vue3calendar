<template>
  <div class="max-w-2xl mx-auto py-16">
    <!-- <Calendar class="w-full" /> -->
    <TagInput />
  </div>
</template>

<script setup lang="ts">
import {defineAsyncComponent} from 'vue'

// const Calendar = defineAsyncComponent(() => import('./components/calendar/index.vue'))
const TagInput = defineAsyncComponent(() => import('./components/tag/TagInput.vue'))
</script>

