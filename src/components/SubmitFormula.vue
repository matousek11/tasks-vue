<script setup lang="ts">
import CustomButton from './Button.vue'
import { ref } from 'vue'

defineProps<{
  addFunction: (text: string) => void
}>()

let text = ref('')

const resetText = () => {
  text.value = ''
}
</script>

<template>
  <div class="container">
    <h1 class="header">Notes</h1>
    <div class="input-container">
      <input placeholder="Task" v-model="text" />
      <CustomButton
        text="Submit"
        color="green"
        @on-press-function="
          () => {
            addFunction(text)
            resetText()
          }
        "
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  z-index: 10;
  position: relative;
}
.header {
  text-align: center;
  font-size: 100px;
  font-weight: 100;
}
.input-container {
  display: flex;
  width: 100%;
  margin-bottom: 10px;
}
input {
  flex-grow: 1;
  margin: 2px;
  margin-left: 0;
  padding-left: 3px;
  border-radius: 4px;
  border: 1px solid lightgray;
  background-color: rgb(253, 253, 253);
  font-size: 20px;
}
</style>
