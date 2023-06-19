<script setup lang="ts">
import Input from './Input.vue'
import CustomButton from './Button.vue'
</script>

<template>
  <div class="container">
    <Input />
    <CustomButton
      text="Submit"
      color="green"
      @on-press-function="
        () => {
          console.log('pressed')
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
</style>
