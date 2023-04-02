<template>
  <h1>Reaction Time</h1>
  <button @click="start" :disabled="isPlaying">Press To Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results :score="score" v-if="showResults"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.isPlaying = true,
      this.delay = 1000 + Math.random() * 3000
      this.showResults = false
      // console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
</style>
