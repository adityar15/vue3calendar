<template>
  <div class="max-w-2xl mx-auto py-16">
    <!-- <Calendar class="w-full" /> -->
    <!-- <TagInput /> -->
    <OTPPad :length="5" @entered="(v)=>otpValue = v"/>

      {{otpValue}}
  </div>
</template>

<script setup lang="ts">
import {defineAsyncComponent, ref} from 'vue'

// const Calendar = defineAsyncComponent(() => import('./components/calendar/index.vue'))
// const TagInput = defineAsyncComponent(() => import('./components/tag/TagInput.vue'))
const OTPPad = defineAsyncComponent(() => import('./components/pin/OTPPad.vue'))


const otpValue = ref('')


</script>

