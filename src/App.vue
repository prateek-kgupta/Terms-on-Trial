<template>
  <div>
    <Welcome
      v-if="instruction"
      class="instrucPage"
      @start="() => (instruction = false)"
    />
    <main-page />
  </div>
</template>

<script>
import Welcome from "./components/Welcome.vue";
import MainPage from "./components/main-page.vue";

export default {
  name: "App",
  data() {
    return {
      instruction: true,
    };
  },
  components: {
    Welcome,
    MainPage,
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
div {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: inherit;
  width: 100%;
}
.instrucPage {
  position: absolute;
  top: 5vh;
  bottom: 5vh;
  width: 70vw;
}
</style>
