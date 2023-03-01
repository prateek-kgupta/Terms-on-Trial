<template>
  <div class="card">
    <h1>GAME OVER</h1>
    <div class="result">
      <h3>Level: {{ level }}</h3>
      <h3>
        You scored: <span>{{ score }}</span>
      </h3>
    </div>
    <div class="action">
      <button
        @click="this.$emit('restart', [level, Math.floor(Math.random() * 50)])"
      >
        Restart
      </button>
      <button @click="this.$emit('changeLevel')">
        Change level and Restart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "gameOver",
  props: {
    score: Number,
    level: String,
  },
  emits: ["restart", "changeLevel"],
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
div.card {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 7%;
}
div.action {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.result {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  padding: 10%;
}
button {
  padding: 10px 20px;
  border-radius: 100px;
  margin: 4px;
  border: 2px solid white;
  color: white;
  background: none;
  outline: none;
  cursor: pointer;
  transition: 0.3s ease-in;
}
button:hover {
  background-color: white;
  color: black;
}
</style>