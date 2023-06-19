<script setup lang="ts">
import CustomButton from './Button.vue'
</script>

<template>
  <div class="container">
    <p class="text">TodoItem</p>
    <div class="button-container">
      <CustomButton text="Done" color="green" />
      <CustomButton text="Delete" color="red" />
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
