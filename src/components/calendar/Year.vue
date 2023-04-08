<template>
  <div class="bg-gray-950 p-3 rounded-t-md grid place-items-center">
    <span class="flex items-center space-x-3 select-none text-gray-50">
      <ChevronLeftIcon class="h-5 w-5 text-gray-400 cursor-pointer" @click="() => modifyYear(-1)" />
      <span>{{ year }}</span>
      <ChevronRightIcon class="h-5 w-5 text-gray-400 cursor-pointer" @click="() => modifyYear(1)" />
    </span>
  </div>
</template>

<script setup lang="ts">
import dayjs from 'dayjs'
import { ref } from 'vue'
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/24/outline'

const yearEmit = defineEmits<{ (e: 'selected', v: number): void }>()

const year = ref<number>(dayjs().year())

function modifyYear(v) {
  year.value += v
  yearEmit('selected', year.value)
}
</script>

