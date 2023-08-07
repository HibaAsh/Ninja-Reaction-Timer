<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />

  <!-- <p v-if="showScore">Reaction Time: {{  score  }} ms</p> -->
  <Results v-if="showScore" :score="score" />
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results, },
  data() {
    return {
      isPlaying: false,
      showScore: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 // between 2s and 7s
      this.isPlaying = true
      this.showScore = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showScore = true
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
  color: #444;
  margin-top: 60px;
}
button{
    border-radius: 4px;
    background: #0faf87;
    color: white;
    border: none;
    text-align: center;
    padding: 8px 16px;
    margin: 10px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
