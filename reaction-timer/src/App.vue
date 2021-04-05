<template>
  <h1>Vue reaction timer</h1>
  <br/>
  <button :disabled="isPlaying" @click="start" >Start reaction game</button>
  <Block v-if="isPlaying" key="blockComponent" :delay='delay' @end-game='showResult'/>
  <Result v-if='showResults && !isPlaying' :result='reactionTime'/>

</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    },
    showResult(reactionTime) {
      this.reactionTime = reactionTime
      this.showResults = true
      this.isPlaying = false
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
</style>
