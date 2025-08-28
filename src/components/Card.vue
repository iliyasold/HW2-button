<script setup>
import {ref} from "vue";
import Button from './Button.vue'
import CardNum from "../icons/CardNum.vue";

// const { word = "word" } = defineProps({
//   word: String,
// });

const Card = ref({
  word: "dust-coat",
  translation: "пыльник",
  state: "closed",
  status: "pending",
})

const reverseButton = () => {
  alert("Перевернулась")
}
</script>

<template>
  <div class="card">
    <div class="card__inner-border">
      <CardNum class="card-number" CardNumber = 6 />

      {{ Card.word }}

      <Button v-if="Card.state === 'closed'" class="reverse__btn card__btn cards-control" @click = "reverseButton">Перевернуть</Button>
       <!-- Или reverse__btn или marks__wrap -->

      <span v-else="Card.state === 'opened'" class="marks__wrap cards-control">
        <Button class="mark__btn ok__btn card__btn" />
        <Button class="mark__btn fail__btn card__btn" />
      </span>
    </div>
  </div>
</template>

<style scoped>
    .card {
      display: flex;
      justify-content: center;
      align-items: center;

      width: 250px;
      min-height: 376px;
      border-radius: 16px;
      -webkit-box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
      -moz-box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
      box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
    }

    .card__inner-border {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-content: space-between;
      align-items: center;
      border: 1px solid var(--bg-color-rate);
      border-radius: 12px;
      width: 212px;
      min-height: 320px;
    }

    .cards-control {
      position: relative;
      width: 100px;
      height: 100%;
      top: 143px;
    }

    .card__btn {
      display: flex;
      justify-content: center;
      background-repeat: no-repeat;
      background-color: white;
    }

    .reverse__btn {
      color: var(--color-primary);
      text-transform: uppercase;
      font-size: 12px;
      font-weight: 700;
    }

    .card-number {
      position: relative;
      top: -135px;
      left: -85px;
      padding: 0 3px;
    }

    .marks__wrap {
      display: flex;
      justify-content: space-between;
      width: 79px;
      padding: 8px 16px;
      background-color: white;
    }

    .mark__btn {
      padding: 0;
      width: 20px;
      height: 20px;
      background-size: 20px;
    }

    .ok__btn {
      background-image: url("../assets/ok.svg");
    }

    .fail__btn {
      background-image: url("../assets/fail.svg");
    }
</style>