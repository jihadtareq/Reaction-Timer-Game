<template>
  <h1>Reaction Timer Game</h1>
  <button  @click="start" :disabled="isPlaying">PLAY</button>
  <MyBlock v-if="isPlaying" :delay="delay" @end="endGame"/>
  <MyResult :score="score" v-if="showResult"/>
  
</template>

<script>
import MyBlock from './components/MyBlock.vue'
import MyResult from './components/MyResults.vue'

export default {
  name: 'App',
  components: { MyBlock ,MyResult },
  data(){
    return{
      isPlaying: false,
      delay:null,
      score:0,
      showResult:false,
    }
  },
  methods:{
    start(){
      // milliseconds
      // 2000 = 2 sec , Math.radom (0-9) so the minimun delay 2000 and the max 7000 it could be between them
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true
      this.showResult=false

    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying=false
      this.showResult=true
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
button {
  background: rgb(87, 200, 163);
  border-radius: 4px;
  border: none;
  color: white;
  padding: 10px 16px;
  margin: 10px;
  cursor: pointer;
  letter-spacing: 1px;

}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
