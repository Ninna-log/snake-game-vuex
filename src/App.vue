<template>
  <div id="app">
    <h1>Snake Game</h1>

    <div class="column">
      Cell size (px):
      <input type="number" min="10" v-model.number="cellSize"/>
    </div>
    <div class="column">
      Board size (cells):
      <input type="number" min="5" v-model.number="boardSize"/>
    </div>
    <div class="column">
      Speed:
      <input type="number" min="1" v-model.number="speed" :isPlaying="isPlaying"/>
    </div>
    <snake-canvas
      :cellSize="cellSize"
      :boardSize="boardSize"
      :speed="speed"
    />
    <div>Scores: {{ scores }}</div>
    <button id="play-btn" v-on:click="isPlaying ? stop() : start()">
      {{ isPlaying ? "Stop" : "Play"}}
    </button>
  </div>
</template>

<script>
import SnakeCanvas from "./components/SnakeCanvas";

export default {
  name: 'App',
  components: {
    SnakeCanvas
  },
  data(){
    return {
      cellSize: 10,
      boardSize: 20,
      speed: 10,
      scores: 0,
      isPlaying: false
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
    },
    stop() {
      this.isPlaying = false;
    }
  }
}
</script>

<style>
*{ box-sizing: border-box; }

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
}
.column {
  display: inline-block;
  width: calc(30% - 5px);
  background-color: #f4f4f4;
  border-radius: 4px;
  padding: 10px 5px;
  margin: 5px;
}
.column input {
  width: 40px;
  border-radius: 4px;
  border: 1px solid #ccc;
  line-height: 20px;
}
#play-btn {
  padding: 10px 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 20px;
  margin-top: 10px;
  cursor: pointer;
}
</style>
