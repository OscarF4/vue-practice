<template>
  <div>
    <b-jumbotron class="py-5">
      <template #lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4">

      <div class="mb-3" v-for="(answer, index) in shuffledAnswers" :key="index"
           @click="selectAnswer(index)" :class="[selectedIndex === index ? 'selected' : '']">
        <button class="btnx">{{ answer }}</button>
      </div>

      <button @click="next" class="blue-btnx">Next</button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: {
      type: Object,
      default() {
        return {
          category: '',
          type: '',
          difficulty: '',
          question: '',
          correct_answer: '',
          incorrect_answers: ''
        }
      }
    },
    next: {
      type: Function
    }
  },
  data() {
    return {
      selectedIndex: null
    }
  },
  computed: {
    shuffledAnswers() {
      let answers = [...this.currentQuestion.incorrect_answers]
      let randomIndex = Math.round(Math.random() * 3)
      answers.splice(randomIndex, 0, this.currentQuestion.correct_answer)
      return answers
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index
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
.selected {
  background-color: lightblue;
}
.correct {
  background-color: lightgreen;
}
.incorrect {
  background-color: red;
}
</style>