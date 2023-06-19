<script setup lang="ts">
defineProps<{
  text: string
  color: string
}>()
</script>

<template>
  <p class="button">{{ text }}</p>
</template>

<style scoped>
.button {
  color: white;
  background-color: v-bind(color);
  margin: 2px 4px;
  padding: 3px 8px;
  border-radius: 4px;
  cursor: pointer;
}
</style>
