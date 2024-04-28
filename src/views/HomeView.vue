<script setup>
import { ref } from 'vue';

const questionText = ref();
const questionList = ref([]);

function askQuestion() {
  if (questionText.value) {
    console.log('Вітаю, твоє питання: ', questionText.value);
    questionList.value = [...questionList.value, questionText.value];
    questionText.value = '';
  }
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
  <h3>
    Мої питання: <span v-if="questionList.length">{{ questionList.length }}</span>
  </h3>
  <ul class="question-list">
    <li v-for="(question, index) in questionList" :key="index" class="question-item">
      {{ index + 1 }} - {{ question }}
    </li>
  </ul>
</template>

<style scoped>
.question-field {
  width: 600px;
  margin: 0 auto;
  padding: 2rem;
  display: flex;
  background: #fbeaff;
  outline: 2px dashed #845ec2;
  outline-offset: -1rem;
  box-sizing: border-box;
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

.question-list {
  width: 600px;
  margin: 0 auto;
  padding: 0;
  list-style: none;
}

.question-item {
  padding: 1rem;
  background: #d4e5ed;
  border-radius: 8px;
  margin-bottom: 1rem;
  list-style: none;
  box-sizing: border-box;
  text-align: left;
}
</style>
