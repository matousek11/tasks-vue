<script setup lang="ts">
import CustomButton from './Button.vue'
import { ref } from 'vue'

defineProps<{
  addFunction: (text: string) => void
}>()

let text = ref('')
</script>

<template>
  <div class="container">
    <input placeholder="Task" v-model="text" />
    <CustomButton
      text="Submit"
      color="green"
      @on-press-function="
        () => {
          addFunction(text)
        }
      "
    />
  </div>
</template>

<style scoped>
.container {
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
