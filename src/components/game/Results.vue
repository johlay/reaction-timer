<template>
  <p v-if="props.showTimerResults === true">
    Reaction time: <span>{{ props.timerResults }} milliseconds</span>
  </p>
</template>

<script>
export default {
  name: "Results",

  props: {
    props: Object,
  },
};
</script>

<style></style>
