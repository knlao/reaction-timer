<template>
  <div class="background" @click.self="checkCheat">
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endgame" />
    <Result v-if="showResult" :score="score" @close="toggleResult" />
    <Cheat v-if="blockCheat" @close="toggleBlockCheat" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
import Cheat from "./components/Cheat.vue";

export default {
  name: "App",
  components: { Block, Result, Cheat },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
      blockCheat: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endgame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
    toggleResult() {
      this.showResult = !this.showResult;
    },
    checkCheat() {
      if (this.isPlaying === true) {
        this.blockCheat = true;
      }
    },
    toggleBlockCheat() {
      this.blockCheat = !this.blockCheat;
      this.isPlaying = false;
    },
  },
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
.background {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0);
  width: 100%;
  height: 100%;
}
</style>
