<template>
    <div class="stopwatch-body">
        <div class="stopwatch-header">
            <h3>{{stopwatch.title }}</h3>
            <button type="button">X</button>
        </div>
        <h1>00:00:00</h1>
        <div class="stopwatch-footer">
            <button type="button">Start</button>
            <button type="button">Reset</button>
            <button type="button">Stop</button>
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