<template>
  <div>
    <b-jumbotron class="py-5">
      <template #lead>
        {{ question.question }}
      </template>

      <hr class="my-4">

      <div class="mb-3" v-for="option in shuffledOptions" :key="option">
        <button class="btnx">{{ option }}</button>
      </div>

      <button class="blue-btnx">Next</button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    question: {
      type: Object,
      required: true
    }
  },
  computed: {
    shuffledOptions() {
      if (this.question) {
        let incorrectAnswers = this.question.incorrect_answers
        let correctAnswer = this.question.correct_answer
        let allAnswers = incorrectAnswers.concat(correctAnswer)
        return allAnswers
      } else {
        this.shuffledOptions()
        return null
      }
    }
  }
}
</script>

<style scoped>
.btnx {
  width: 100%;
  padding: 0.375rem 0.75rem;
  border: 1px solid #212529;
  color: #212529;
  background-color: transparent;
  border-radius: 5px;
}
.btnx:hover {
  background-color: #212529;
  color: white;
}
.blue-btnx {
  width: 100%;
  padding: 0.375rem 0.75rem;
  border: 1px solid rgb(0,106,255);
  color: white;
  background-color: rgb(0,106,255);
  border-radius: 5px;
}
.blue-btnx:hover {
  background-color: rgb(0,81,230);
}
</style>