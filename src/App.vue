<template>
  <h1>open code reaction timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <!-- <p v-if="showResult">Reaction: {{score}} ms</p> -->
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Result.vue'


export default {
  name: 'App',
  components: {Block,Results},
  data(){
    return{
      delay: null,
      isPlaying: false,
      showResult : false,
      score: null
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  background: #0faf87;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  letter-spacing: 1px;
  margin: 10px;
}
button[disabled]{
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
