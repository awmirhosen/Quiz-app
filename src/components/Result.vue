<template>
  <div class="result">
    <div class="title">
      {{ results[handleResult].title }}
    </div>
    <div class="desc">
      {{ results[handleResult].desc }}
    </div>

  </div>
</template>

<script setup>
import {computed} from "vue";
import {ref} from "@vue/reactivity";

const props = defineProps([
    "results", "correctQuestions"
])

const handleResult = computed(() => {
  let index = 0;

  props.results.forEach((item, i) => {
    console.log(props.correctQuestions, item.min)
    if (item.min <= props.correctQuestions && item.max >= props.correctQuestions){
      index = i
      console.log(props.correctQuestions, item.min)
    }
  })

  return index
})


</script>

<style scoped>

</style>