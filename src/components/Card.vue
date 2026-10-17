<script setup lang="ts">
defineProps<{
  cardRussian: string;
  cardEnglish: string;
  cardReverse: boolean;
  cardNumber: number;
  status: "pending" | "success" | "fail";
}>();

const emit = defineEmits<{
  flip: [];
  "set-status": [status: "success" | "fail"];
}>();
</script>

<template>
  <div class="card" @click="emit('flip')">
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
        <template v-if="status === 'pending'">
          <button
            class="card__button"
            type="button"
            @click.stop="emit('set-status', 'success')"
          >
            Да
          </button>

          <button
            class="card__button"
            type="button"
            @click.stop="emit('set-status', 'fail')"
          >
            Нет
          </button>
        </template>

        <div v-else-if="status === 'success'">Верно!</div>

        <div v-else>Неверно</div>
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
