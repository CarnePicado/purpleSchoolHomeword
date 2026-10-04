<script setup lang="ts">
import { ref } from "vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

const val = ref(0);
const cardNum = 1;

const isReverse = ref(false);

const status = ref<"pending" | "success" | "fail">("pending");

const setStatus = (newStatus: "success" | "fail") => {
  status.value = newStatus;
};

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
    :status="status"
    @flip="isCardReversed"
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
