<template>
  <Navbar />
  <Stopwatches/>
  <Footer />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Stopwatches from "./components/Stopwatches.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Stopwatches,
    Footer,
  },
};
</script>

<style>
body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background-color: #121212;
    margin: 0;
    box-sizing: border-box;
    color: white;
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    line-height: 1.42857143;
    padding-right: 10%;
    padding-left: 10%;
    margin-right: auto;
    margin-left: auto;
}
</style>
