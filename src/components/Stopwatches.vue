<template>
  <div class="navbar text-center">
    <input v-model="title" placeholder="Add Your Task" />
    <button
      id="button-add"
      type="button"
      class="zen-font thick-font"
      @click="addstopwatch"
    >
      NEW
    </button>
    <button
      id="delete-all"
      type="button"
      class="zen-font thick-font"
      @click="deleteall"
    >
      DELETE ALL
    </button>
  </div>
  <div class="zen-font">
    <div class="container-stopwatch">
      <Stopwatch
        v-for="(stopwatch, index) in stopwatches"
        :key="index"
        :title="stopwatch.title"
        :timeBegan="stopwatch.timeBegan"
        :timeStopped="stopwatch.timeStopped"
        :stoppedDuration="stopwatch.stoppedDuration"
        :started="stopwatch.started"
        :running="stopwatch.running"
        :jam="stopwatch.jam"
        :last="stopwatch.last"
        @delete="deleteStopwatch(index)"
        @start="start(index)"
        @stop="stop(index)"
        @reset="reset(index)"
      />
    </div>
  </div>
</template>

<script>
import Stopwatch from "./Stopwatch.vue";
export default {
  name: "Stopwatches",
  components: {
    Stopwatch,
  },
  data() {
    return {
      stopwatches: [],
      title: "",
    };
  },
  methods: {
    deleteall() {
      this.stopwatches = [];
    },
    addstopwatch() {
      if (this.title == "") {
        this.title = "Untitled";
      }
      this.stopwatches.push({
        title: this.title,
        timeBegan: null,
        timeStopped: null,
        stoppedDuration: 0,
        started: null,
        running: false,
        jam: "00:00:00.000",
        last: "Total: 00 Hours 00 Minutes 00 Seconds",
      });
      this.title = "";
    },
    deleteStopwatch(index) {
      this.stopwatches.splice(index, 1);
    },
    start(index) {
      console.log(index);
      if (this.stopwatches[index].running === true) {
        return;
      }
      for (let i = 0; i < this.stopwatches.length; i++) {
        if (i !== index && this.stopwatches[i].running) {
          this.stop(i);
        }
      }

      if (this.stopwatches[index].timeBegan === null) {
        this.reset(index);
        this.stopwatches[index].timeBegan = new Date();
      }

      if (this.stopwatches[index].timeStopped !== null) {
        this.stopwatches[index].stoppedDuration +=
          new Date() - this.stopwatches[index].timeStopped;
      }

      this.stopwatches[index].started = setInterval(this.stopwatchRunning, 10);
      this.stopwatches[index].running = true;
    },
    stop(index) {
      if (this.stopwatches[index].running === false) {
        return;
      }
      console.log(index);
      this.stopwatches[index].running = false;
      this.stopwatches[index].timeStopped = new Date();
      console.log(this.stopwatches[index].timeStopped);
      clearInterval(this.stopwatches[index].started);
    },
    reset(index) {
      console.log(index);
      this.lastTime(index);
      this.stopwatches[index].running = false;
      clearInterval(this.stopwatches[index].started);
      this.stopwatches[index].stoppedDuration = 0;
      this.stopwatches[index].timeBegan = null;
      this.stopwatches[index].timeStopped = null;
      this.stopwatches[index].jam = "00:00:00.000";
    },
    lastTime(index) {
      if (this.stopwatches[index].timeBegan === null) {
        this.stopwatches[index].last = "Total: 00 Hours 00 Minutes 00 Seconds";
        return;
      }
      this.stopwatches[index].timeBegan = new Date(
        this.stopwatches[index].timeBegan
      );
      var currentTime = new Date();
      if (this.stopwatches[index].running) {
        currentTime = new Date();
      } else {
        currentTime = new Date(this.stopwatches[index].timeStopped);
      }
      var timeElapsed = new Date(
          currentTime -
            this.stopwatches[index].timeBegan -
            this.stopwatches[index].stoppedDuration
        ),
        hour = timeElapsed.getUTCHours(),
        min = timeElapsed.getUTCMinutes(),
        sec = timeElapsed.getUTCSeconds();
      this.stopwatches[index].last =
        "Total: " +
        this.zeroPrefix(hour, 2) +
        " Hours " +
        this.zeroPrefix(min, 2) +
        " Minutes " +
        this.zeroPrefix(sec, 2) +
        " Seconds ";
    },
    stopwatchRunning() {
      for (var i = 0; i < this.stopwatches.length; i++) {
        if (this.stopwatches[i].running === true) {
          this.stopwatches[i].timeBegan = new Date(
            this.stopwatches[i].timeBegan
          );
          var currentTime = new Date(),
            timeElapsed = new Date(
              currentTime -
                this.stopwatches[i].timeBegan -
                this.stopwatches[i].stoppedDuration
            ),
            hour = timeElapsed.getUTCHours(),
            min = timeElapsed.getUTCMinutes(),
            sec = timeElapsed.getUTCSeconds(),
            ms = timeElapsed.getUTCMilliseconds();
          this.stopwatches[i].jam =
            this.zeroPrefix(hour, 2) +
            ":" +
            this.zeroPrefix(min, 2) +
            ":" +
            this.zeroPrefix(sec, 2) +
            "." +
            this.zeroPrefix(ms, 3);
          return (
            "Total: " +
            this.zeroPrefix(hour, 2) +
            " Hours " +
            this.zeroPrefix(min, 2) +
            " Minutes " +
            this.zeroPrefix(sec, 2) +
            " Seconds"
          );
        }
      }
    },
    zeroPrefix(num, digit) {
      var zero = "";
      for (var i = 0; i < digit; i++) {
        zero += "0";
      }
      return (zero + num).slice(-digit);
    },
    saveClock() {
      localStorage.setItem("stopwatches", JSON.stringify(this.stopwatches));
    },
  },
  created() {
    window.addEventListener("beforeunload", () => {
      this.saveClock();
    });
  },
  mounted() {
    if (localStorage.getItem("stopwatches") !== null) {
      this.stopwatches = JSON.parse(localStorage.getItem("stopwatches"));
    } else {
      this.addstopwatch();
    }
    for (var i = 0; i < this.stopwatches.length; i++) {
      this.stopwatches[i].timeBegan = new Date(this.stopwatches[i].timeBegan);
      this.stopwatches[i].timeStopped = new Date(
        this.stopwatches[i].timeStopped
      );
      if (this.stopwatches[i].running) {
        this.stopwatches[i].started = setInterval(this.stopwatchRunning, 10);
      } else {
        this.stopwatches[i].timeStopped = new Date(
          this.stopwatches[i].timeStopped
        );
      }
    }
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+Antique:wght@300&display=swap");

.zen-font {
  font-family: "Zen Kaku Gothic Antique", sans-serif;
}

.navbar {
  position: relative;
  margin: auto;
  padding-bottom: 20px;
  display: flex;
  justify-content: center;
  color: white;
  border-bottom: 1px solid #eee;
}

input{
  float: left;
  width: 60%;
  color: white;
  width: 50%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border-radius: 24px;
  border: none;
  outline: none;
  color: white;
  border: 4px solid white;
  background: none;
  transition: 0.5s;
}

input::placeholder{
  width: 55%;
}

input:focus{
  border: 4px solid #ffffff;
  color: white;
}

input:focus::placeholder{
  color: white;
}

.thick-font {
  font-weight: bold;
}

button[type="button"] {
  color: white;
  padding: 12px 20px;
  padding-left: -50px;
  cursor: pointer;
  border-radius: 20px;
  border: none;
  position: relative;
  display: block;
  transition: 0.5s;
}



#button-add {
  float: left;
  color: white;
  padding: 12px 20px;
  padding-left: -50px;
  text-decoration: none;
  margin: 8px 0;
  cursor: pointer;
  border-radius: 24px;
  border: 4px solid white;
  background: black;
  transition: 0.5s;
}

#button-add:hover{
  background: white;
  border: 4px solid white;
  color: black;
}

button[type="button"]:hover {
  background-color: white;
  color: black;
}

#delete-all {
  float: left;
  color: white;
  font-size: inherit;
  background-color: #da0037;
  padding: 12px 20px;
  padding-left: -50px;
  text-decoration: none;
  margin: 8px 0;
  cursor: pointer;
  border-radius: 24px;
  border: 4px solid #da0037;
  transition: 0.5s;
}

#delete-all:hover{
  background: white;
  border: 4px solid white;
  color: #d9534f;
}

</style>