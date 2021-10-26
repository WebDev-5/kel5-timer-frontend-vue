<template>
  <Navbar />
  <StopwatchForm />
  <Stopwatches/>
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
};
</script>

<style>
</style>
