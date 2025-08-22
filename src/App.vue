<script setup>
  import Button from "./components/Button.vue";
  import Header from "./components/Header.vue";

  import Card from "./components/Card.vue";
</script>

<template>
  <Header />
  <main class="main">
    <Button>Начать игру</Button>

    <Card word = "dust-coat" />
  </main>
</template>

<style scoped>

</style>
