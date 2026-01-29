<template>
  <h1> Reaction Timer</h1>

  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @game-over="end" />
  <Results v-if="showResults" :score="score"/>
  <History :score="score" :isplaying="isPlaying"/>

</template>

<script>
import Block from './Components/Block.vue';
import Results from './Components/Results.vue';
import History from './Components/History.vue';

export default {
  name: 'App',
  components: { Block, Results, History },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },

  methods:{
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 4000;
      this.showResults = false
      console.log("Game started");
    }, 
    end(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
      console.log("Game ended");
  }
  }
}
</script>

<style>
#app{
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:#444;
  margin-top:60px;
}
</style>
