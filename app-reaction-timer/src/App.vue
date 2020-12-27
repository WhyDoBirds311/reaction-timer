<template>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
     <Block v-if="isPlaying" :delay="delay" @end="endGame" />
     <Result v-if="showResults" :score="score"></Result>
</template>

<script>
import Block from './components/blocks.vue'
import Result from './components/results.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    } 
  },
  methods: {
    start() {
      this.isPlaying = true
      this.delay  = 2000 + Math.random() * 5000
    },
    endGame(reactionTime) {
      this.score = reactionTime
      console.log(this.score)
      this.isPlaying = false
      this.showResults = true;
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
