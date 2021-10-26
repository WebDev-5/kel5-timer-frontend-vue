<template>
    <div class="stopwatch-body">
        <div class="stopwatch-header">
            <h3 id="title">{{stopwatch.title }}</h3>
            <button id="remove" type="button">X</button>
        </div>
        <br>
        <h1 class="jam">00:00:00</h1>
        <h3 class="total_jam">Total: 0 Hours 0 Minutes 0 Seconds</h3>
        <!-- <div class="stopwatch-time">
            <h1 id="jam">00:00:00</h1>
        </div> -->
        <div class="stopwatch-footer">
            <button id="start_btn" type="button">Start</button>
            <button id="pause_btn" type="button">Reset</button>
            <button id="restart_btn" type="button">Stop</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Stopwatch",
    props: {
        stopwatch: Array,
    }
};
</script>

<style scoped>

</style>