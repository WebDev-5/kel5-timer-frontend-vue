<template>
  <div class="container-stopwatch">
    <div class="stopwatch-body">
      <div class="stopwatch-header">
        <h3 id="title">Stopwatch</h3>
        <button id="remove" type="button">X</button>
      </div>
      <br />
      <br />
      <h1 class="text-center tech-font">{{ clock.jam }}</h1>
      <h3 class="total_jam">{{ clock.last }}</h3>
      <div class="stopwatch-footer">
        <button class="the_btn" type="button" v-on:click="start()">
          Start
        </button>
        <button class="the_btn" type="button" v-on:click="stop()">Stop</button>
        <button class="the_btn" type="button" v-on:click="reset()">
          Reset
        </button>
      </div>
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
        last: "Total: 00 Hours 00 Minutes 00 Seconds",
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
      this.last();
      clearInterval(this.clock.started);
      this.clock.stoppedDuration = 0;
      this.clock.timeBegan = null;
      this.clock.timeStopped = null;
      this.clock.jam = "00:00:00.000";
    },
    last() {
      if (this.clock.timeBegan === null) {
        this.clock.last = "Total: 00 Hours 00 Minutes 00 Seconds";
        return;
      }
      var currentTime = new Date();
      if (this.clock.timeStopped === null) {
        currentTime = new Date();
      } else {
        currentTime = this.clock.timeStopped;
      }
      var timeElapsed = new Date(
          currentTime - this.clock.timeBegan - this.clock.stoppedDuration
        ),
        hour = timeElapsed.getUTCHours(),
        min = timeElapsed.getUTCMinutes(),
        sec = timeElapsed.getUTCSeconds();
      console.log(currentTime.getUTCHours());
      console.log(hour);
      this.clock.last =
        "Total: " +
        this.zeroPrefix(hour, 2) +
        " Hours " +
        this.zeroPrefix(min, 2) +
        " Minutes " +
        this.zeroPrefix(sec, 2) +
        " Seconds";
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
  created() {
    localStorage.setItem("stopwatch", JSON.stringify(this.clock));
  },
  mounted() {
    this.clock = JSON.parse(localStorage.getItem("stopwatch"));
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Share+Tech+Mono");

.tech-font {
  font-family: "Share Tech Mono", sans-serif;
}

.text-center {
  text-align: center;
}

.container-stopwatch {
  padding-top: 2%;
}

.stopwatch-body {
  border: 3px solid #da0037;
  border-radius: 24px;
  margin: 5px;
  margin-right: 6px;
  position: relative;
  min-height: 1px;
  padding-right: 18px;
  padding-left: 18px;
  width: 45%;
  float: left;
  /* background-color: crimson; */
}

.stopwatch-header {
  /* padding: 10px 15px; */
  border-bottom: 1px solid transparent;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  height: 16px;
}

#title {
  /* background-color: aqua; */
  float: left;
  /* width: 40%; */
  color: white;
}

#remove {
  /* background-color: aqua; */
  margin-top: 10px;
  float: right;
  /* width: 40%; */
  /* color: white; */
}

.stopwatch-time {
  background-color: #155799;
  height: 30px;
  /* padding: 15px; */
}

.total_jam {
  text-align: center;
}

.stopwatch-footer {
  float: left;
  width: 100%;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 3px;
  border-bottom-left-radius: 3px;
}

#start_btn:hover {
  background-color: #da0037;
  color: white;
}

.the_btn {
  float: left;
  background: #444444;
  width: 33%;
}

.the_btn:hover {
  background-color: #da0037;
  color: white;
}

#start_btn {
  float: left;
  background: #444444;
  width: 33%;
}

#pause_btn:hover {
  background-color: #da0037;
  color: white;
}

#pause_btn {
  float: left;
  background: #444444;
  width: 34%;
  /* display: none; */
}

#restart_btn:hover {
  background-color: #da0037;
  color: white;
}

#restart_btn {
  float: left;
  background: #444444;
  width: 33%;
  /* display: none; */
}
</style>