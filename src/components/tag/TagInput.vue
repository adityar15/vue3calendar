<template>
  <div class="w-full my-6">
    <div class="flex flex-wrap h-20 items-center gap-4 border border-gray-200 rounded-md p-3 overflow-x-hidden overflow-y-auto
    hover:ring hover:ring-purple-400 transition-all ease-in-out duration-150">
        <span v-for="(t, i) in tags" :key="i" class="flex items-center p-2 bg-gray-400/50 rounded-md space-x-2">
            <span class="text-gray-800">
                {{t}}
            </span>
            <XMarkIcon class="w-4 h-4 stroke-gray-600" @click="() => removeTag(i)"/>
        </span>

        <input type="text" class="flex-grow h-full outline-none border-none" v-model="tag" @keydown="manageKeyPress" placeholder="tag here ..." />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'

const tags = ref<string[]>(['vue', 'react'])

const tag = ref<string>('')

function removeTag(index: number) {
  tags.value.splice(index, 1)
}

function addTag() {
  let v = tag.value.trim()
  if (v === '') return

  tags.value = [...tags.value, v]
  tag.value = ''
}

function manageKeyPress(e) {
  if (e.key === 'Enter') addTag()
  else if (e.key === 'Backspace' && tag.value=="") tags.value.pop()
}
</script>

<style scoped></style>
