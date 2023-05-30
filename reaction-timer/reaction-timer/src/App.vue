<template>
  <h1> Reaction timer app </h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <div v-if="isPlaying">
    <Block :prop_timer_delay="delay" @game_over="game_over_methond"></Block>
  </div>
  <div  v-if="isOver">
    <Result :prop_result="score" ></Result>
  </div>
</template>

<script>
import Block from './components/block.vue'
import Result from './components/result.vue'

export default {
  name: 'App',
  components: {Block,Result},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isOver: null
    }
  },
  methods: {
    start() {
      this.isPlaying = true
      this.score = null
      this.isOver = null
      this.delay = 2000 + Math.random() * 5000
      console.log("delay is ", this.delay)
    },
    game_over_methond(reactionTime) {
      console.log("Game over")
      this.isPlaying=false
      this.score = reactionTime
      this.isOver = true
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
