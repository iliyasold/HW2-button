<script setup>
import Score from './Score.vue';

</script>

<template>
  <header class="header">
    <h1 class="top-title">Запомни слово</h1>

    <Score score = 100 />
  </header>
</template>

<style scoped>
  .header {
    display: flex;
    justify-content: space-between;
    padding: 20px 40px;
  }
</style>