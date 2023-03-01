<template>
  <div class="mHead">
    <h3><i>Terms-on-Trial</i></h3>
    <button @click="showLevels()" class="level-btn">Select Levels</button>
    <div v-if="choose" class="options">
      <span @click="selectOption('Easy')">Easy</span>
      <span @click="selectOption('Medium')">Medium</span>
      <span @click="selectOption('Hard')">Hard</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "main-header",
  emits: ["lvl"],
  data() {
    return {
      choose: false,
    };
  },

  methods: {
    showLevels() {
      this.choose = !this.choose;
    },
    selectOption(gameLevel) {
      const randomNum = Math.floor(Math.random() * 50);
      this.$emit("lvl", [gameLevel, randomNum]);
      this.choose = !this.choose;
    },
  },
};
</script>

<style scoped>
.mHead {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  background-color: #1c2541;
  padding: 5px;
  padding-left: 20px;
}
.level-btn {
  background: none;
  color: white;
  font-size: 16px;
  padding: 3px 10px;
  height: 70%;
  margin-right: 20px;
  border: none;
  border-bottom: 1px solid white;
  cursor: pointer;
  transition: 0.2s ease-in;
  top: 10px;
  right: 10px;
  cursor: pointer;
}
.options {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: fixed;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  top: 70px;
  right: 25px;
  padding: 15px;
  background-color: #1c2541d7;
  border: 1px solid white;
  border-radius: 5px;
  flex-wrap: wrap;
}
.options span {
  margin: 5px;
  padding: 7px 10px;
  text-align: center;
  border: none;
  border-bottom: 1px solid white;
  cursor: pointer;
}
button:hover {
  border-bottom: 3px solid white;
  font-size: 18px;
}
h3 {
  color: white;
  font-size: 24px;
  font-family: Century Gothic;
  font-weight: bolder;
}
</style>