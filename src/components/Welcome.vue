<template>
  <div>
    <h1>WELCOME TO <i class="appName">Terms-on-Trial</i></h1>

    <ul>
      <h2 class="instruction">Instructions:</h2>
      <li>Choose the difficulty level which suits you</li>
      <li>
        After you select the level, the cursor will automatically point to the
        input field
      </li>
      <li>Type the word shown within the given time</li>
      <li>Score will be increased by <b>1</b> after each correct submission</li>
    </ul>
    <button @click="this.$emit('start')">Lets Go!!</button>
  </div>
</template>

<script>
export default {
  name: "welcome-page",
  emits: ["start"],
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
div {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  border: 2px solid white;
  border-radius: 15px;
  background-color: #1c2541f0;
  color: white;
  margin: 20px;
  padding: 5%;
  box-shadow: 1px 14px 20px 8px rgba(40, 35, 35, 0.55);
}
.appName {
  font-family: Century Gothic;
  font-weight: bolder;
}
ul {
  text-align: left;
}
li {
  margin: 1px;
  font-size: 20px;
}
.instruction {
  text-decoration: underline;
  margin-bottom: 8px;
}
button {
  font-weight: bold;
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