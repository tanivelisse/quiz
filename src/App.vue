<template>
  <div id="app">
    <Header msg="Welcome to Your Vue.js App"/>
    <Questions msg="Welcome to Your Vue.js App"
      v-if="questions.length"
      :currentQuestion= "questions[index]"
      :next="next"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Questions from  './components/Questions.vue'

export default {
  name: 'App',
  components: {
    Header,
    Questions
  },
  data() {
    return {
      questions:[],
      index: 0
    }
  },
  methods: {
    next() {
      this.index++
    }
  },
  mounted: function() {
    fetch ('https://opentdb.com/api.php?amount=10&category=27&difficulty=easy',{
      method:'get'
    })
      .then((response)=> {
        return response.json()
      })
      .then((jasonData) => {
        this.questions = jasonData.results
      })
  }
}
</script>

<style lang="css">
@import '../src/assets/style.css';
</style>
