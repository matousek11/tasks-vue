<script setup lang="ts">
import ToDoItem from './components/ToDoItem.vue'
import { ref } from 'vue'
import SubmitFormula from './components/SubmitFormula.vue'
import { v4 as uuidv4 } from 'uuid'

type NoteObj = {
  id: string
  text: string
  done: boolean
}

let array = ref<NoteObj[]>([])

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
  <div class="main-container">
    <div class="glassomorphism"></div>
    <div class="app-container">
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
  </div>
</template>

<style scoped>
.main-container {
  width: 100vw;
  height: 100vh;
  background-image: url('/bubles.jpg');
  display: flex;
  justify-content: center;
  align-items: center;
}
.glassomorphism {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.25);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(6px);
  -webkit-backdrop-filter: blur(6px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
}
.app-container {
  margin: 5px;
}
.app-container .todoScroll {
  padding-top: 5px;
  padding-bottom: 5px;
  position: relative;
  height: 300px;
  overflow-y: scroll;
  overflow-x: visible;
}
</style>
