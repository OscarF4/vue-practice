<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b>Fancy Quiz</b></b-nav-item>
      <b-nav-item disabled>Counter: {{ numCorrect }}/{{ numTotal }}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: {
    currentCounter: {
      type: Number,
      default: 1
    },
    numCorrect: {
      Type: Number
    },
    numTotal: {
      Type: Number
    }
  }
}
</script>