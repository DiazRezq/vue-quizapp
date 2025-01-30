<script setup>
import QuizContent from "@/components/QuizContent.vue";
import QuizHeader from "@/components/QuizHeader.vue";
import { useRoute } from "vue-router";
import quizes from "../data/quizez.json";
import { computed, ref } from "vue";
import QuizResult from "../components/QuizResult.vue";
const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizes.find((q) => q.id === quizId);
const numberCorrectAnswers = ref(0);

const currentQuestionIndex = ref(0);
const showResult = ref(false);
const questionPage = computed(
  () => `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`
);

const barProgress = computed(() => {
  return `${(currentQuestionIndex.value + 1 / quiz.questions.length) * 100}%`;
});

function onSelectedOption(option) {
  if (option.isCorrect) {
    numberCorrectAnswers.value++;
  }

  if (currentQuestionIndex.value === quiz.questions.length - 1) {
    showResult.value = true;
    return;
  }

  currentQuestionIndex.value++;
}
</script>

<template>
  <QuizHeader :questionPage="questionPage" :barProgress="barProgress" />
  <QuizContent
    v-if="!showResult"
    :question="quiz.questions[currentQuestionIndex]"
    @selectedOption="onSelectedOption"
  />

  <QuizResult v-else :quizlenght="quiz.questions.length" :numberCorrectAnswers="numberCorrectAnswers" />
</template>

<style scoped></style>
