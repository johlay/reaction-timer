<template>
  <div class="timer-block" v-if="showTimerBlock" @click="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
  name: "Timer",

  // Lifecycle Hooks
  mounted() {
    // Show "game block" when reactionDelay is completed.
    setTimeout(() => {
      // Set showTimerBlock to: true.
      this.showTimerBlock = true;

      // Start timer.
      this.startTimer();
    }, this.props.reactionDelay);
  },

  data() {
    return {
      reactionTime: 0,
      showTimerBlock: false,
      timer: null,
    };
  },

  methods: {
    startTimer() {
      // Every 10 milliseconds - add +10ms to variable: "reactionTime".
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    stopTimer() {
      // Clears the timer after user has clicked on "timer block".
      clearInterval(this.timer);

      // Emit event to App component.
      this.$emit("end", this.reactionTime);
    },
  },

  props: {
    props: Object,
  },
};
</script>

<style scoped>
.timer-block {
  background: #53b8bb;
  border-radius: 5px;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  margin: 40px auto;
  padding: 100px 200px;
  text-align: center;
}
</style>
