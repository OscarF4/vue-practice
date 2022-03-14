<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled><b>Fancy Quiz</b></b-nav-item>
      <b-nav-item disabled>Question: {{ currentCounter }}/10</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: {
    currentCounter: {
      type: Number,
      default: 1
    }
  }
}
</script>