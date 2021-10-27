<template>
<div class="zen-font">
    <Stopwatch/>
</div>
</template>

<script>
import Stopwatch from './Stopwatch.vue'
export default {
    name: "Stopwatches",
    components: {
        Stopwatch,
    },
    data() {
        return {
            stopwatches: [],
        }
    },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+Antique:wght@300&display=swap');

.zen-font {
    font-family: 'Zen Kaku Gothic Antique', sans-serif;
}
</style>