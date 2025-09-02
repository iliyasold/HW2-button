<script setup>
import { reactive } from "vue";
import Button from "./Button.vue";
import CardNum from "../icons/CardNum.vue";

const props = defineProps({
  card: { type: Object, required: true },
  index: { type: Number, required: true }
});

// Делаем объект карточки реактивным
const cardReactive = reactive(props.card);

// Переворот карточки
const toggleButton = () => {
  if (cardReactive.state === "closed" && cardReactive.status === "pending") {
    cardReactive.state = "opened";
  } else if (cardReactive.state === "opened" && cardReactive.status !== "pending") {
    cardReactive.state = "closed";
    cardReactive.status = "pending";
  }
};

// Проверка ответа
const answer = (isRight) => {
  cardReactive.status = isRight ? "success" : "fail";
};
</script>

<template>
  <li class="card">
    <div class="card__inner-border">
      <CardNum class="card-number" :CardNumber="index" />

      <Button class="mark__btn card__btn mark__result no_btn"
              :class="{
                'ok__btn': cardReactive.status === 'success' && cardReactive.state === 'opened',
                'fail__btn': cardReactive.status === 'fail' && cardReactive.state === 'opened',
                'transparent': cardReactive.state === 'closed' || (cardReactive.state === 'opened' && cardReactive.status === 'pending'),
              }" />

      {{ cardReactive.state === 'closed' ? cardReactive.word : cardReactive.translation }}

      <Button v-if="cardReactive.state === 'closed'"
              class="reverse__btn card__btn cards-control"
              @click="toggleButton">
        Перевернуть
      </Button>

      <Button v-if="cardReactive.state === 'opened' && cardReactive.status !== 'pending'"
              class="reverse__btn card__btn cards-control"
              @click="toggleButton">
        Завершить
      </Button>

      <span v-if="cardReactive.state === 'opened' && cardReactive.status === 'pending'"
            class="marks__wrap cards-control">
        <Button class="ok__btn mark__btn card__btn" @click="answer(true)" />
        <Button class="fail__btn mark__btn card__btn" @click="answer(false)" />
      </span>
    </div>
  </li>
</template>

<style scoped>
.card {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 250px;
  min-height: 376px;
  border-radius: 16px;
  box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
}

.card__inner-border {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 1px solid var(--bg-color-rate);
  border-radius: 12px;
  width: 212px;
  min-height: 320px;
}

.cards-control {
  position: relative;
  top: 125px;
  width: 98px;
  height: 100%;
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
  top: -117px;
  left: -85px;
  padding: 0 3px;
}

.marks__wrap {
  display: flex;
  justify-content: space-between;
  width: 79px;
  padding: 6px 5px 5px 5px;
  background-color: white;
}

.mark__btn {
  padding: 0;
  width: 20px;
  height: 20px;
  background-size: 20px;
}

.mark__result {
  position: relative;
  top: -143px;
  width: 36px;
  height: 36px;
  background-size: 36px;
}

.no_btn {
  cursor: default;
}

.no_btn:hover {
  opacity: 1;
}

.ok__btn {
  background-image: url("../assets/ok.svg");
}

.fail__btn {
  background-image: url("../assets/fail.svg");
}

.transparent {
  background: transparent;
}
</style>
