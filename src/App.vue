<template>
  <Navbar />
  <StopwatchForm />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import StopwatchForm from "./components/StopwatchForm.vue";

export default {
  name: "App",
  components: {
    Navbar,
    StopwatchForm,
  },
};
</script>

<style>
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #63b4b8;
  margin: 0;
  box-sizing: border-box;
  color: white;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 14px;
  line-height: 1.42857143;
}
</style>
