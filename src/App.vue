<template>
  <Navbar />
  <StopwatchForm />
  <Footer/>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import StopwatchForm from "./components/StopwatchForm.vue";
import Footer from "./components/Footer.vue"

export default {
  name: "App",
  components: {
    Navbar,
    StopwatchForm,
    Footer,
  },
};
</script>

<style>
</style>
