<template>
  <div class="timer-block" v-if="showTimerBlock">Click me</div>
</template>

<script>
export default {
  name: "Timer",

  // Lifecycle Hooks
  mounted() {
    // Show "game block" when reactionDelay is completed.
    setTimeout(() => {
      // set showTimerBlock to: true.
      this.showTimerBlock = true;
    }, this.props.reactionDelay);
  },

  data() {
    return {
      showTimerBlock: false,
    };
  },

  methods: {},

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
