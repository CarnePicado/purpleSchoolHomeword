<script setup lang="ts">
import { ref } from "vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

const val = ref(0);
const cardNum = 1;

const isReverse = ref(false);

const increment = () => {
  val.value++;
};

const isCardReversed = () => {
  isReverse.value = true;
};
</script>

<template>
  <div class="header">
    <div>Запомни слово</div>

    <Score :val="val" @click="increment" />
  </div>

  <Card
    :card-number="cardNum"
    card-english="hello"
    card-russian="привет"
    :card-reverse="isReverse"
    @click="isCardReversed"
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
}
</style>
