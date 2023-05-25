<template>
  <ComboBox :dataSet="people" v-model="selectedPerson" targetKey="name" />

  <!-- modal -->

  <div class="">
    <button
      type="button"
      @click="openModal"
      class="rounded-md bg-black bg-opacity-20 px-4 py-2 text-sm font-medium text-white hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
    >
      Submit
    </button>
  </div>

  <Modal :isOpen="isOpen" @closeModal="isOpen = false">
    <template #title> Sending Invoice ... </template>
    <template #content>
      <p class="text-sm text-gray-500">Invoide is on the way for {{ selectedPerson.name }} ...</p>
    </template>
  </Modal>


</template>

<script setup>
import { ref, defineAsyncComponent } from 'vue'

const ComboBox = defineAsyncComponent(() => import('./ComboBox.vue'))

const Modal = defineAsyncComponent(() => import('./Modal.vue'))

const people = [
  { name: 'Wade Cooper' },
  { name: 'Arlene Mccoy' },
  { name: 'Devon Webb' },
  { name: 'Tom Cook' },
  { name: 'Tanya Fox' },
  { name: 'Hellen Schmidt' }
]
const selectedPerson = ref(people[0])

// modal

const isOpen = ref(true)


function openModal() {
  isOpen.value = true
}
</script>
