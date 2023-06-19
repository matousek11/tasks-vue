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
    <div class="todoScroll">
      <ToDoItem
        :id="item.id"
        :text="item.text"
        :done="item.done"
        :doneFunction="() => handleDone(item.id)"
        :deleteFunction="() => handleDelete(item.id)"
        v-for="item in array"
      />
    </div>
  </div>
</template>

<style scoped>
.todoScroll {
  padding-top: 40px;
  padding-bottom: 40px;
  position: relative;
  height: 400px;
  overflow-y: scroll;
}
.todoScroll::before,
.todoScroll::after {
  content: ' ';
  display: none;
  position: absolute;
  width: 100%;
  height: 100px;
  z-index: 10;
  pointer-events: none;
}
.todoScroll::before {
  top: 0;
  background-image: linear-gradient(white, rgba(0, 0, 0, 0));
}
.todoScroll::after {
  bottom: 0;
  background-image: linear-gradient(rgba(0, 0, 0, 0), white);
}
</style>
