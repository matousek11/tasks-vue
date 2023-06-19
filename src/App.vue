<script setup lang="ts">
import ToDoItem from './components/ToDoItem.vue'
import { ref } from 'vue'

const array = ref([
  { id: '1', text: 'string', done: false },
  { id: '2', text: 'string2', done: true }
])
</script>

<template>
  <div>
    <ToDoItem :id="item.id" :text="item.text" :done="item.done" v-for="item in array" />
  </div>
</template>

<style scoped></style>
