<template>
  <form class="text-center">
    <input
      id="title"
      type="text"
      class="baloo-font"
      placeholder="Enter Title for Stopwatch ..."
    />
    <input id="addWatch-btn" type="submit" class="baloo-font" value="ADD" />
    <button id="removeAll_btn">REMOVE ALL</button>
  </form>
  <hr />
</template>

<script>
export default {
  name: "StopwatchForm",
};
</script>

<style scoped>
@import '../assets/style.css';
</style>
