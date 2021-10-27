<template>
  <div class="stopwatch-body">
    <div class="stopwatch-header">
      <h3 id="title">{{ title }}</h3>
      <button @click="onDelete()" id="remove" type="button">X</button>
    </div>
    <br />
    <br />
    <h1 class="text-center tech-font timer">{{ jam }}</h1>
    <h3 class="total_jam">{{ last }}</h3>
    <div class="stopwatch-footer">
      <button @click="start()" class="the_btn" type="button">Start</button>
      <button @click="stop()" class="the_btn" type="button">Stop</button>
      <button @click="reset()" class="the_btn" type="button">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Stopwatch",
  props: {
    id: Number,
    title: String,
    timeBegan: Date,
    timeStopped: Date,
    stoppedDuration: Number,
    started: Number,
    running: Boolean,
    jam: String,
    last: String,
  },
  methods: {
    onDelete() {
      this.$emit("delete");
    },
    start(){
      this.$emit("start")
    },
    stop(){
      this.$emit("stop");
    },
    reset(){
      this.$emit("reset");
    }
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

.timer {
  font-size: 30px;
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
  background: #155799;
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