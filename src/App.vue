<template>
<div>
  <h4>Completed Project</h4>
  <h3>Reaction Timer</h3>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>

  <Results v-if="showResults" :score="score"/>



</div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'


export default {
    name: 'App',
    data() {
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false
    }
  },
  components: {
    Block,
    Results,
  },
  methods:
  {
    start()
    {
    this.isPlaying=true;
    this.delay=2000+Math.random()*5000;
    console.log(this.delay);
    this.showResults=false;
    },
    endGame(reactionTime)
    {
      this.isPlaying=false;
      this.score=reactionTime;
      this.showResults=true;
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
