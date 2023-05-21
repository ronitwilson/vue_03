<template>
  <h1> Reaction timer app </h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <div v-if="isPlaying">
    <Block :prop_timer="delay"></Block>
  </div>
</template>

<script>
import Block from './components/block.vue'

export default {
  name: 'App',
  components: {Block},
  data() {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 * Math.random() * 5000
      console.log("delay is ", this.delay)
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
