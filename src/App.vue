<template>
  <main>
    <h1>Reaction Timer ⏲</h1>
    <div class="button-wrapper">
      <button @click="start" :disabled="isStarting">Start timer</button>
      <button @click="instruction">Instructions</button>
    </div>
    <hr />
    <Timer v-if="isStarting" :props="{ reactionDelay }" @end="end" />
    <Results :props="{ timerResults, showTimerResults }" />
  </main>
</template>

<script>
import Timer from "./components/game/Timer.vue";
import Results from "./components/game/Results.vue";

export default {
  name: "App",

  components: { Timer, Results },

  data() {
    return {
      isStarting: false,
      reactionDelay: null,
      timerResults: null,
      showTimerResults: false,
    };
  },

  methods: {
    start() {
      // Hide results.
      this.showTimerResults = false;

      // Sets the delay of game reaction between: 2-7 seconds.
      this.reactionDelay = 2000 + Math.random() * 5000;

      // Starts the game by setting "isStarting" to: true.
      this.isStarting = true;

      return;
    },

    end(reactionTime) {
      // Result.
      this.timerResults = reactionTime;

      // Show result.
      this.showTimerResults = true;

      // Ends the timer by setting "isStarting" to: false.
      this.isStarting = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Roboto, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

hr {
  margin: 2rem;
  margin-left: auto;
  margin-right: auto;
  width: 75%;
}
</style>
