<script setup lang="ts">
import ToDoItem from './components/ToDoItem.vue'
import { ref } from 'vue'
import SubmitFormula from './components/SubmitFormula.vue'
import { v4 as uuidv4 } from 'uuid'

const array = ref([
  { id: '1', text: 'string', done: false },
  { id: '2', text: 'string2', done: false }
])

const handleAddFormula = (text: string) => {
  let randomId = uuidv4()
  array.value = [...array.value, { id: randomId, text: text, done: false }]
}

const handleDone = (id: string) => {
  array.value.map((item) => (item.id === id ? (item.done = !item.done) : (item.done = item.done)))
}

const handleDelete = (id: string) => {
  array.value = array.value.filter((item) => (item.id === id ? false : true))
}
</script>

<template>
  <div>
    <SubmitFormula :addFunction="handleAddFormula" />
    <ToDoItem
      :id="item.id"
      :text="item.text"
      :done="item.done"
      :doneFunction="() => handleDone(item.id)"
      :deleteFunction="() => handleDelete(item.id)"
      v-for="item in array"
    />
  </div>
</template>

<style scoped></style>
