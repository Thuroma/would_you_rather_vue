<template>
  <div class="wyr">

    <h2>{{ question.question }}</h2>

    <input type="radio" v-model="choice" v-bind:value="question.answer1" v-on:change="choiceMade(question.id, question.answer1, $event.target.checked)">
    <label>{{ question.answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="question.answer2" v-on:change="choiceMade(question.id, question.answer2, $event.target.checked)">
    <label>{{ question.answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRatherQuestion',
  props: {
    question: String,
    answer1: String,
    answer2: String,
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    choiceMade(id, answer) {
      this.$emit('answer-changed', id, answer)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr {
  border: 2px black solid;
  background-color: lightseagreen;
}
</style>
