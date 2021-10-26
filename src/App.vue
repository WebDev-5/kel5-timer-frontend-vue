<template>
  <Navbar />
  <StopwatchForm />
  <Stopwatches :stopwatches="stopwatches"/>
  <Footer />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import StopwatchForm from "./components/StopwatchForm.vue";
import Stopwatches from "./components/Stopwatches.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Navbar,
    StopwatchForm,
    Stopwatches,
    Footer,
  },
  data() {
    return {
      stopwatches: [],
    };
  },
  created() {
    this.stopwatches = [
      {
        id: 1,
        isRunning: 0,
        title: "Faza",
        startTime: 1635220395601,
        timeDelays: 0,
        pauseTime: 1635220398563,
        continueTime: 0,
      },
      {
        id: 2,
        isRunning: 0,
        title: "Untitled 2",
        startTime: 0,
        timeDelays: 0,
        pauseTime: 0,
        continueTime: 0,
      },
      {
        id: 3,
        isRunning: 0,
        title: "Untitled 3",
        startTime: 1635220389362,
        timeDelays: 6074,
        pauseTime: 1635220400981,
        continueTime: 1635220398563,
      },
      {
        id: 4,
        isRunning: 0,
        title: "Untitled 4",
        startTime: 1635220392489,
        timeDelays: 0,
        pauseTime: 1635220395601,
        continueTime: 0,
      },
      {
        id: 5,
        isRunning: 0,
        title: "Untitled 5",
        startTime: 1635220392489,
        timeDelays: 0,
        pauseTime: 1635220395601,
        continueTime: 0,
      },
    ];
  },
};
</script>

<style>
</style>
