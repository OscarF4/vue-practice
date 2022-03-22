<template>
  <div>
    <b-jumbotron class="py-5">
      <template #lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4">

      <div class="mb-3" v-for="(answer, index) in shuffledAnswers" :key="index"
           @click="submitAnswer(index)"
           :class="{ correct: selectedAnswer && answer === currentQuestion.correct_answer,
        incorrect: selectedAnswer && answer !== currentQuestion.correct_answer }">
        <button class="btnx">{{ answer }}</button>
      </div>

      <b-button block variant="success" @click="next">
        Next
      </b-button>
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
    },
    increment: {
      type: Function
    },
    selectedAnswer: {
      type: Boolean
    },
    selectedState: {
      type: Function
    }
  },
  data() {
    return {
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
    submitAnswer(index) {
      this.selectedState()
      if (this.shuffledAnswers[index] === this.currentQuestion.correct_answer) {
        this.increment(true)
      } else {
        this.increment(false)
      }

      // let isCorrect = false
      //
      // if (this.shuffledAnswers[this.selectedIndex] === this.currentQuestion.correct_answer) {
      //   isCorrect = true
      // }
      // this.answered = true
      //
      // this.increment(isCorrect)
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
  background-color: inherit;
  opacity: 0.6;
  /*color: white;*/
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
  background-color: lawngreen;
  transition: 1s;
}
.incorrect {
  background-color: red;
  transition: 1s;
}
</style>