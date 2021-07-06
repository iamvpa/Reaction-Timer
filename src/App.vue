<template>
<div>
<h1>Ninja Reaction timer</h1>
  <button @click="start" :disabled="isPlaying" >play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <p v-if="showResults">Reaction time:{{score}} ms</p>
</div>
  
</template>

<script>
import Block from "./components/Block";
export default {
  name: "App",
  components: { Block },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.showResults = true;
      this.score = reactionTime;
      this.isPlaying = false;
      console.log(this.score);
    }
  }
};
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
