<script setup>
import Button from "./components/Button.vue";
import Header from "./components/Header.vue";
import CardList from "./components/CardList.vue";
import { ref } from "vue";

// Массив карточек
const cards = ref([
  { word: "car", translation: "автомобиль", state: "closed", status: "pending" },
  { word: "neighbour", translation: "сосед", state: "closed", status: "pending" },
  { word: "dust-coat", translation: "пыльник", state: "closed", status: "pending" },
  { word: "morning", translation: "утро", state: "closed", status: "pending" },
]);
</script>

<template>
  <Header />
  <main class="main">
    <Button>Начать игру</Button>
    <CardList :cards="cards" />
  </main>
</template>

<style scoped>
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}
</style>
