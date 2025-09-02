<script setup>
import { defineProps } from "vue";
import CardItem from "./CardItem.vue";

const props = defineProps({
  cards: {
    type: Array,
    required: true
  }
});
</script>

<template>
  <ul class="card-list">
    <CardItem
        v-for="(card, index) in props.cards"
        :key="index"
        :card="card"
        :index="index + 1"
    />
  </ul>
</template>

<style scoped>
.card-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  padding: 0;
  list-style: none;
}
</style>
