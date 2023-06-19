<script setup lang="ts">
import CustomButton from './Button.vue'

defineProps<{
  todoItem: string
}>()

const handleDone = () => {
  console.log('Done')
}

const handleDelete = () => {
  console.log('Delete')
}
</script>

<template>
  <div class="container">
    <p class="text">{{ todoItem }}</p>
    <div class="button-container">
      <CustomButton text="Done" color="green" @on-press-function="handleDone" />
      <CustomButton text="Delete" color="red" @on-press-function="handleDelete" />
    </div>
  </div>
</template>

<style scoped>
.container {
  min-width: 250px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgb(253, 253, 253);
  border: 1px solid lightgrey;
  border-radius: 5px;
  padding: 4px 8px;
}
.button-container {
  display: flex;
}
</style>
