<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";
const { numberCorrectAnswers, quizlenght } = defineProps([
  "numberCorrectAnswers",
  "quizlenght",
]);
</script>

<template>
  <section class="result">
    <p>Score:</p>
    <h1>{{ numberCorrectAnswers }} / {{ quizlenght }}</h1>
    <router-link to="/"><button>Back</button></router-link>
  </section>
</template>

<style scoped>
.result {
  text-align: center;
  margin-top: 50px;
  padding: 20px;
}

p {
  font-size: 50px;
}
h1 {
  font-size: 80px;
}
</style>
