<template>
  <div id="app">
    <!-- Whatever Vue is managing goes in this div -->
    
    <h1>Would you rather??</h1>

    <!-- These are the different parts that are managed by the would-you-rather component 
    When answer-changed happens in would-you-rather, answerChanged is called in the methods -->
    <would-you-rather-question 
      v-for="question in questions"
      v-bind:question="question"
      v-on:answer-changed="answerChanged">
    </would-you-rather-question>

    <h2>Your answers:</h2>
    <ul>
      <li v-for="selection in userSelectionsList">{{ selection.answerChoice }}</li>
    </ul>

  </div>
</template>

<script>
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion: WouldYouRatherQuestion
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question: 'Would you rather have a magic carpet that flies or a see-through submarine?',
          answer1: 'Flying magic carpet',
          answer2: 'See-through submarine',
        },
        {
          id: 1,
          question: 'Would you rather sail a boat or ride in a hang glider?',
          answer1: 'Sail a boat',
          answer2: 'Ride in a hang glider',
        },
        {
          id: 2,
          question: 'Would you rather eat an apple or an orange?',
          answer1: 'Eat an apple',
          answer2: 'Eat an orange',
        }
      ],
      userSelectionsList: []
    }
  },
  methods: {
    answerChanged(id, answer) {

      let choiceMade = this.userSelectionsList.find(function(q) {
        if (q.answerID === id)
          return true
      })

      if (choiceMade) {
        choiceMade.answerChoice = answer
      } else {
        this.userSelectionsList.push({answerID: id, answerChoice: answer})
      }

      this.userSelectionsList.sort(function(q1, q2) {
        return q1.answerID < q2.answerID ? -1 : 1
      })
      
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
  background: rgb(148, 225, 221);
}

li {
  background: rgb(148, 225, 221);
}
</style>
