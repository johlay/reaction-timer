<template>
  <main>
    <h1>Reaction Timer ⏲</h1>
    <div class="button-wrapper">
      <button @click="start" :disabled="isStarting">Start timer</button>
      <button @click="instruction">Instructions</button>
    </div>
    <Play v-if="isStarting" :props="{ reactionDelay }" />
  </main>
</template>

<script>
import Play from "./components/game/Timer.vue";

export default {
  name: "App",

  components: { Play },

  data() {
    return {
      isStarting: false,
      reactionDelay: null,
    };
  },

  methods: {
    start() {
      // Sets the delay of game reaction between: 2-7 seconds.
      this.reactionDelay = 2000 + Math.random() * 5000;

      // Starts the game by setting "isStarting" to: true.
      this.isStarting = true;

      return;
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
</style>
