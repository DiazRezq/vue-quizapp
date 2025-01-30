<script setup>
import { defineProps } from "vue";

const { question } = defineProps(["question"]);

const emit = defineEmits(["selectedOption"]);

function emitSelectedOption(option) {
  emit("selectedOption", option);
}
</script>

<template>
  <section id="question-container">
    <h1 class="question-title">{{ question.text }}</h1>
  </section>
  <section id="option-container">
    <div
      class="option"
      v-for="option in question.answers"
      :key="option.id"
      @click="emitSelectedOption(option)"
    >
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">{{ option.text }}</div>
    </div>
  </section>
</template>

<style scoped>
.question-container {
  margin-top: 30px;
}

.question-title {
  font-size: 40px;
  margin-bottom: 20px;
  font-weight: bold;
}

.option-group {
  display: flex;
  gap: 10px 20px; /* row-gap column gap */
  row-gap: 10px;
  column-gap: 20px;
}

.option {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.option-label {
  width: 50px;
  height: 50px;
  background-color: #ccc;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 20px;
  font-size: 20px;
  font-weight: bold;
}

.option-value {
  font-size: 20px;
  font-weight: bold;
  color: #666;
  width: 100%;
}
</style>
