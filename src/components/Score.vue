<script setup lang="ts">
defineProps<{
  val: number;
}>();

const emit = defineEmits<{
  click: [];
}>();
</script>

<template>
  <div class="score" @click="emit('click')">{{ val }} Лайков</div>
</template>

<style scoped>
.score {
  display: inline-flex;
  cursor: pointer;
  border: 1px solid black;
}
</style>
