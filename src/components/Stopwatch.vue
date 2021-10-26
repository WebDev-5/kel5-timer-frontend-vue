<template>
  <div class="stopwatch-body">
    <div class="stopwatch-header">
      <h3 id="title">Stopwatch</h3>
      <button id="remove" type="button">X</button>
    </div>
    <br />
    <br />
    <h1 class="jam">{{ clock.jam }}</h1>
    <h3 class="total_jam">Total: 0 Hours 0 Minutes 0 Seconds</h3>
    <!-- <div class="stopwatch-time">
            <h1 id="jam">00:00:00</h1>
        </div> -->
    <div class="stopwatch-footer">
      <button id="the_btn" type="button" v-on:click="start()">Start</button>
      <button id="the_btn" type="button" v-on:click="reset()">Reset</button>
      <button id="the_btn" type="button" v-on:click="stop()">Stop</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Stopwatch",
  data() {
    return {
      clock: {
        timeBegan: null,
        timeStopped: null,
        stoppedDuration: 0,
        started: false,
        running: false,
        jam: "00:00:00.000",
      },
    };
  },
  methods: {
    start() {
      if (this.clock.running) return;

      if (this.clock.timeBegan === null) {
        this.reset();
        this.clock.timeBegan = new Date();
      }

      if (this.clock.timeStopped !== null) {
        this.clock.stoppedDuration += new Date() - this.clock.timeStopped;
      }

      this.clock.started = setInterval(this.clockRunning, 10);
      this.clock.running = true;
    },
    stop() {
      this.clock.running = false;
      this.clock.timeStopped = new Date();
      clearInterval(this.clock.started);
    },
    reset() {
      this.clock.running = false;
      clearInterval(this.clock.started);
      this.clock.stoppedDuration = 0;
      this.clock.timeBegan = null;
      this.clock.timeStopped = null;
      this.clock.jam = "00:00:00.000";
    },
    clockRunning() {
      var currentTime = new Date(),
        timeElapsed = new Date(
          currentTime - this.clock.timeBegan - this.clock.stoppedDuration
        ),
        hour = timeElapsed.getUTCHours(),
        min = timeElapsed.getUTCMinutes(),
        sec = timeElapsed.getUTCSeconds(),
        ms = timeElapsed.getUTCMilliseconds();
      console.log(this.clock.stoppedDuration);
      this.clock.jam =
        this.zeroPrefix(hour, 2) +
        ":" +
        this.zeroPrefix(min, 2) +
        ":" +
        this.zeroPrefix(sec, 2) +
        "." +
        this.zeroPrefix(ms, 3);
    },
    zeroPrefix(num, digit) {
      var zero = "";
      for (var i = 0; i < digit; i++) {
        zero += "0";
      }
      return (zero + num).slice(-digit);
    },
  },
  created(){
      localStorage.setItem('stopwatch', JSON.stringify(this.clock));
  },
  mounted(){
      this.clock = JSON.parse(localStorage.getItem('stopwatch'));
  },
};
</script>

<style scoped>
</style>