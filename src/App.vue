<template>
  <div id="app">
    <HeaderBox :currentCounter="currentCounter" />

    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox :question="currentQuestion" />
        </b-col>
      </b-row>
  </b-container>
  </div>
</template>

<script>
import HeaderBox from './components/HeaderBox.vue'
import QuestionBox from './components/QuestionBox.vue'

export default {
  name: 'App',
  components: {
    HeaderBox,
    QuestionBox
  },
  data() {
    return {
      currentCounter: 1,
      questions: [],
      currentQuestion: {}
    }
  },
  mounted() {
    fetch('https://opentdb.com/api.php?amount=10&category=27&type=multiple', {
      method: 'get'
    })
      .then((response) => {
        return response.json()
      })
      .then((jsonData) => {
        this.questions = jsonData.results
        this.assignQuestion()
      })
  },
  methods: {
    assignQuestion() {
      this.currentQuestion = this.questions[this.currentCounter - 1];
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.red {
  color: red;
}
</style>
