<script setup>
import { defineProps } from "vue";
const { questionPage, barProgress } = defineProps([
  "questionPage",
  "barProgress",
]);
</script>

<template>
  <header>
    <h4>{{ questionPage }}</h4>
    <div class="bar">
      <div class="bar-progress" :style="{ width: barProgress }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
}

header h4 {
  font-size: 40px;
}

.bar {
  width: 100%;
  height: 50px;
  background-color: #ccc;
  margin-top: 10px;
  border-radius: 5px;
  position: relative;
  overflow: hidden;
}

.bar-progress {
  height: 100%;
  width: 0;
  background-color: green;
}
</style>
