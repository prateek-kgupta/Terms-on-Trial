<template>
  <div class="mPage">
    <main-header @lvl="(val) => setLevel(val)" />
    <div class="workspace">
      <span class="subHead" v-if="!level">Select Level</span>
      <span class="subHead" v-else>{{ contestWord }}</span>
      <input
        class="answer"
        placeholder="Answer Space"
        type="text"
        v-model="typedWord"
        ref="ansBox"
      />
      <div class="counter">
        <span>Time Left: {{ timeLeft ? `${timeLeft} seconds` : "-/-" }}</span>
        <span>Score: {{ score }}</span>
      </div>
    </div>
    <game-over
      class="overCard"
      v-show="isGameOver"
      :score="score"
      :level="level"
      @restart="(prevLevel) => setLevel(prevLevel)"
      @changeLevel="resetGame()"
    />
  </div>
</template>

<script>
import mainHeader from "./main-header.vue";
import gameOver from "./game-over.vue";

export default {
  name: "main-page",
  data() {
    return {
      level: null,
      prevIndex: -1,
      wordIndex: -1,
      contestWord: "",
      score: 0,
      timeLeft: 0,
      typedWord: "",
      allowedTime: null,
      isGameOver: false,
      words: [
        "serene",
        "quintessential",
        "jubilant",
        "frivolous",
        "transient",
        "effervescent",
        "resilient",
        "frenetic",
        "scintillating",
        "furtive",
        "melancholy",
        "ubiquitous",
        "inevitable",
        "ephemeral",
        "pensive",
        "reticent",
        "elusive",
        "expedient",
        "idiosyncratic",
        "luminous",
        "quixotic",
        "retrospective",
        "turbulent",
        "verdant",
        "vivacious",
        "pleasant",
        "relax",
        "simple",
        "sincere",
        "curious",
        "friendly",
        "robust",
        "doubtful",
        "resistant",
        "poor",
        "show",
        "clean",
        "accidental",
        "extra",
        "mysterious",
        "echo",
        "essential",
        "temporary",
        "hopeful",
        "deep",
        "bright",
        "cautious",
        "uncertain",
        "prove",
        "beginner",
      ],
    };
  },
  components: {
    mainHeader,
    gameOver,
  },
  methods: {
    setLevel(val) {
      this.isGameOver = false;
      this.score = 0;
      this.level = val[0];
      const difficulty = this.level;
      this.wordIndex = val[1];
      this.prevIndex = this.wordIndex;
      this.contestWord = this.words[this.wordIndex];
      this.$refs.ansBox.focus();
      if (difficulty == "Easy") {
        this.allowedTime = 15;
      } else if (difficulty == "Medium") {
        this.allowedTime = 10;
      } else {
        this.allowedTime = 5;
      }
      this.timeLeft = this.allowedTime;
      const timer = setInterval(() => {
        this.timeLeft--;
        if (this.timeLeft <= 0) {
          clearInterval(timer);
          this.typedWord = "";
          this.isGameOver = true;
        }
      }, 1000);
    },
    resetGame() {
      this.level = null;
      this.prevIndex = -1;
      this.wordIndex = -1;
      this.contestWord = "";
      this.score = 0;
      this.timeLeft = 0;
      this.typedWord = "";
      this.allowedTime = null;
      this.isGameOver = false;
    },
  },
  watch: {
    typedWord(newValue) {
      if (newValue === this.contestWord && this.timeLeft > 0) {
        this.score++;
        this.timeLeft = this.allowedTime;
        this.wordIndex = Math.floor(Math.random() * 50);
        if (this.wordIndex === this.prevIndex) {
          this.wordIndex = (this.wordIndex + 1) % 50;
        }
        this.prevIndex = this.wordIndex;
        this.contestWord = this.words[this.wordIndex];
        this.typedWord = "";
      }
    },
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.mPage {
  display: flex;
  background-color: #758bfd;
  color: white;
  height: 100vh;
  align-items: center;
}
.workspace {
  /* margin: 0 auto; */
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  align-items: center;
  padding-bottom: 20px;
}
.subHead {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  font-size: 50px;
  font-weight: bold;
  margin-top: 100px;
}
.answer {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  margin-top: 70px;
  width: 70%;
  height: 40px;
  padding: 2px;
  font-size: xx-large;
  outline: none;
  color: white;
  text-align: center;
  border: none;
  background: none;
  border-bottom: 2px solid white;
}

.counter {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  margin-top: 30px;
  width: 70%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 20px;
  font-weight: bold;
}
.overCard {
  position: absolute;
  top: 25vh;
  width: 50vh;
  height: 50vh;
  background-color: #1c2541f0;
  box-shadow: 1px 14px 20px 8px rgba(40, 35, 35, 0.55);
}
</style>