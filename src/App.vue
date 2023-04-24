<template>
  <div id="app">
    <!-- Whatever Vue is managing goes in this div -->
    
    <h1>Would you rather??</h1>

    <!-- These are the different parts that are managed by the would-you-rather component 
    When answer-changed happens in would-you-rather, answerChanged is called in the methods -->
    <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather>

    <p>{{ userSelectionMessage }}</p>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather have a magic carpet that flies or a see-through submarine?',
      wyrAnswer1: 'Flying magic carpet',
      wyrAnswer2: 'See-through submarine',
      userSelectionMessage: ''
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}`
    }
  }
}
</script>

<style>
body {
  background: lightslategray;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: lightskyblue;
}
</style>
