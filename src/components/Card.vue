<script setup lang="ts">
defineProps<{
  cardRussian: string;
  cardEnglish: string;
  cardReverse: boolean;
  cardNumber: number;
}>();

const emit = defineEmits<{
  click: [];
}>();
</script>

<template>
  <div class="card" @click="emit('click')">
    <div class="card__content">
      <div class="card__number">
        {{ cardNumber }}
      </div>

      <div class="card__word">
        <template v-if="!cardReverse">
          {{ cardEnglish }}
        </template>

        <template v-else>
          {{ cardRussian }}
        </template>
      </div>

      <div v-if="!cardReverse" class="card__action">Перевернуть</div>

      <div v-else class="card__actions">
        <button class="card__button" type="button" @click.stop>Да</button>

        <button class="card__button" type="button" @click.stop>Нет</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 150px;
  height: 300px;

  background-color: grey;
  border-radius: 4px;
}

.card__content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  width: 100%;
  height: 100%;
  padding: 16px;

  box-sizing: border-box;

  border: 1px solid black;
  border-radius: 4px;
}

.card__number {
  font-size: 14px;
}

.card__word {
  text-align: center;
  font-size: 24px;
}

.card__action {
  cursor: pointer;

  border: none;
  background: none;

  text-align: center;
}

.card__actions {
  display: flex;
  justify-content: center;
  gap: 16px;
}

.card__button {
  cursor: pointer;

  padding: 8px 16px;

  border: 1px solid black;
  border-radius: 4px;

  background-color: white;
}
</style>
