<script setup>
import { ref } from 'vue';
import Heart from "../icons/Heart.vue";

// const { score = 0 } = defineProps({
//       score: Number,
//     });

const score = ref(100)
</script>

<template>
  <div class="stat">
    <span>{{ score }}</span>

    <Heart />
  </div>
</template>

<style scoped>
  .stat {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 12px 24px;
    gap: 10px;
    font-size: 17px;
    font-weight: 700;
    color: var(--bg-color-btn);
    background-color: var(--bg-color-rate);
    border-radius: 25px;
    -webkit-box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
    -moz-box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
  }
</style>