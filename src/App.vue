<script setup lang="ts">
import { ref } from "vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

interface ICard {
  word: string;
  translation: string;
  state: "closed" | "opened";
  status: "success" | "fail" | "pending";
}

const val = ref(0);

const cards = ref<ICard[]>([
  {
    word: "hello",
    translation: "привет",
    state: "closed",
    status: "pending",
  },
]);

const increment = () => {
  val.value++;
};

const flipCard = () => {
  cards.value[0].state = "opened";
};

const setStatus = (newStatus: "success" | "fail") => {
  cards.value[0].status = newStatus;
};
</script>

<template>
  <div class="header">
    <div>Запомни слово</div>

    <Score :val="val" @click="increment" />
  </div>

  <Card
    :card-number="1"
    :word="cards[0].word"
    :translation="cards[0].translation"
    :state="cards[0].state"
    :status="cards[0].status"
    @flip="flipCard"
    @set-status="setStatus"
  />
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;

  width: 100%;
  max-width: 1440px;
  margin: 0 auto;

  padding: 16px 24px;

  border-bottom: 1px solid #000;
}

.header > div:first-child {
  font-size: 24px;
  font-weight: 600;
}
</style>
