<script setup lang="ts">
import CustomButton from './Button.vue'

defineProps<{
  id: string
  text: string
  done: boolean
  doneFunction: () => void
  deleteFunction: () => void
}>()
</script>

<template>
  <div class="container">
    <div class="dark-container" v-bind:style="done === true ? '' : 'display: none;'"></div>
    <p class="text">{{ text }}</p>
    <div class="button-container">
      <CustomButton text="Done" color="green" @on-press-function="doneFunction" />
      <CustomButton text="Delete" color="red" @on-press-function="deleteFunction" />
    </div>
    <hr class="line" v-bind:style="done == true ? '' : 'display: none;'" />
  </div>
</template>

<style scoped>
.container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  min-width: 250px;
  background-color: rgb(253, 253, 253);
  margin-bottom: 5px;
  padding: 4px 8px;
  border: 1px solid lightgrey;
  border-radius: 5px;
}
.dark-container {
  position: absolute;
  left: -1px;
  width: 100%;
  height: 100%;
  min-width: 250px;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  z-index: 10;
  pointer-events: none;
}
.button-container {
  display: flex;
}
.line {
  position: absolute;
  left: -10%;
  width: 120%;
  height: 1px;
  color: transparent;
  background-color: black;
  border-color: transparent;
  pointer-events: none;
}
</style>
