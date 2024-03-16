<template>
  <h1>Reaction Time</h1>
  <button @click="play" class="play" :disabled="isPlaying">PLAY</button>
  <Box v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="score" :score="score"/>
</template>

<script>
import Result from './components/Result.vue'
import Box from './components/Box.vue'

export default {
  name: 'App',
  components: {
    Result,
    Box
  },
  data(){
    return {
      isPlaying: false,
      delay : null,
      score : null
    }
  },
  methods: {
    play(){
      this.delay = Math.random() * 3000 + 1000
      this.isPlaying = true
      this.score = null
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
    }
  }
}
</script>

<style>
  h1{
    color: #444;
  }
</style>
