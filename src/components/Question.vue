<template>

  <div class="questions-ctr">
    <div class="progress">
      <div class="bar" :style="{ width : `${(questionCount / questions.length) * 100 }%` }"></div>
      <div class="status">
        {{ questionCount }} out of {{ questions.length }} questions answered
      </div>
    </div>
    <div class="single-question"
         v-for="(question, index) in questions"
         :key="index"
         v-show="props.questionCount == index"
    >
      <div class="question">{{ question.q }}</div>

      <div class="answers">
        <div class="answer"
             v-for="answer in question.answers"
             :key="answer.text"
             @click.prevent="selectAnswer(answer.is_correct)"
        >
          {{answer.text}}
        </div>

      </div>
    </div>
  </div>

</template>

<script setup>

import {computed} from "vue";

const props = defineProps([
    "questions", "questionCount"
])
const emits = defineEmits([
    'selectAnswer'
])

const questions = props.questions

const selectAnswer = (is_correct) => {
  emits("selectAnswer", is_correct)
}

</script>

<style scoped>

</style>