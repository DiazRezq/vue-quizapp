<script setup>
import { ref, watch } from "vue";
import srcQuiz from "../data/quizez.json";
import QuizCard from "../components/QuizCard.vue";

const quizes = ref(srcQuiz);
const search = ref("");

watch(search, () => {
  quizes.value = srcQuiz.filter((quiz) =>
    quiz.title.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <main>
    <header>
      <h1 id="title">vueQuiz</h1>
      <input v-model.trim="search" type="text" id="search-input" />
    </header>
    <section id="quiz-container">
      <QuizCard
        v-for="quiz in quizes"
        :key="quiz.id"
        :quiz="quiz"
        :quizes="quizes"
      />
    </section>
  </main>
</template>

<style scoped>

header {
  margin-top: 30px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

#title {
  font-weight: bold;
  margin-right: 30px;
}

#search-input {
  border: none;
  background-color: #b6b1b1;
  padding: 10px;
  border-radius: 5px;
}

#quiz-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 20px;
}
</style>
