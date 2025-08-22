<script setup lang="ts">
const { CardNumber = 0 } = defineProps({
  CardNumber: Number,
});
</script>

<template>
  <span class="card-number">
    {{ CardNumber }}
  </span>
</template>

<style scoped>
  .card-number {
    background-color: white;
    font-weight: 400;
    font-size: 14px;
  }
</style>