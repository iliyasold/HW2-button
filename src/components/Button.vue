<script setup>

</script>

<template>
  <button class="button">
    <slot />
  </button>
</template>

<style scoped>
  .button {
    width: 335px;
    height: 68px;
    padding: 8px 16px;
    border-radius: 35px;
    font-family: var(--font), serif;
    font-size: 24px;
    font-weight: 400;
    background: var(--bg-color-btn);
    color: var(--color-btn);
  }

  .button:hover {
    opacity: 0.8;
  }
</style>