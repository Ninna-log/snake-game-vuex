<template>
  <div id="app">
    <h1>Snake Game</h1>

    <div class="column">
      Cell size (px):
      <input type="number" min="10"/>
    </div>
    <div class="column">
      Board size (cells):
      <input type="number" min="5"/>
    </div>
    <div class="column">
      Speed:
      <input type="number" min="1"/>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
 
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
  width: 30px;
  border-radius: 4px;
  border: 1px solid #ccc;
  line-height: 20px;
}
</style>
