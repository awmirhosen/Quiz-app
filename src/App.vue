<template>
  <div class="ctr">
    <question v-if="questionCount < questions.length"
              :questions="questions"
              :questionCount="questionCount"
              @selectAnswer="handleAnswers"
    />
    <result v-else
            :correctQuestions="correctQuestions"
            :results="results"
    />
    <button type="button" class="reset-btn" @click.prevent="handleResetButton">Reset</button>
  </div>
</template>

<script setup>
import { ref, reactive } from "@vue/reactivity";
import "./assets/main.css";
import Question from "./components/Question.vue";
import Result from "./components/Result.vue";

const questionCount = ref(0)
const correctQuestions = ref(0)

const handleResetButton = () => {
  questionCount.value = 0;
  correctQuestions.value = 0
}

const handleAnswers = (is_correct) => {
  console.log()
  if (is_correct) {
    correctQuestions.value ++;
    console.log(correctQuestions.value)
  }

  questionCount.value++;
}

const questions = reactive([
  {
    q: '2 + 2 * 4?',
    answers: [
      {
        text: '10',
        is_correct: true
      },
      {
        text: '16',
        is_correct: false
      },
      {
        text: '2',
        is_correct: false
      },
      {
        text: '8',
        is_correct: false
      }
    ]
  },
  {
    q: '4 / 2 + 2',
    answers: [
      {
        text: '1',
        is_correct: false
      },
      {
        text: '2',
        is_correct: false
      },
      {
        text: '4',
        is_correct: true
      },
      {
        text: '10',
        is_correct: false
      }
    ]
  },
  {
    q: '5 * 5 + 6 * 2',
    answers: [
      {
        text: '25',
        is_correct: false
      },
      {
        text: '37',
        is_correct: true
      },
      {
        text: '62',
        is_correct: false
      }
    ]
  },
],)

const results = reactive([
  {
    min: 0,
    max: 1,
    title: "Try again!",
    desc: "Do a little more studying and you may succeed!"
  },
  {
    min: 2,
    max: 3,
    title: "Wow, you're a genius!",
    desc: "Studying has definitely paid off for you!"
  }
])


</script>

<style>



</style>
