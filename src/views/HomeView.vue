<script setup>
import { ref } from 'vue';

const questionText = ref();

function askQuestion() {
  console.log('Вітаю, твоє 1 питання: ', questionText.value);
  questionText.value = '';
}
</script>

<template>
  <h2>Реактивність Vue на прикладі</h2>
  <div class="question-field">
    <input
      v-model="questionText"
      placeholder="Запитай мене щось про Vue"
      @keyup.enter="askQuestion"
    />
    <button @click="askQuestion">Запитати</button>
  </div>
  <h3>Мої питання</h3>
  <p>{{ questionText }}</p>
</template>

<style scoped>
.question-field {
  min-width: 400px;
  padding: 2rem;
  display: flex;
  background: #fbeaff;
  outline: 2px dashed #845ec2;
  outline-offset: -1rem;
}

input {
  width: 100%;
  padding: 1rem;
  border: 0;
  border-radius: 8px 0 0 8px;
  outline: none;
  font-size: 1.1rem;
}

button {
  border-radius: 0 8px 8px 0;
  background: #4d8076;
  color: #fff;
  outline: none;

  &:hover {
    background: #005b44;
  }
}
</style>
