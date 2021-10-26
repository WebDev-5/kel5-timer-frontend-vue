<template>
<div :key="stopwatch.id" v-for="stopwatch in stopwatches" class="zen-font">
    <Stopwatch :stopwatch="stopwatch"/>
</div>
</template>

<script>
import Stopwatch from './Stopwatch.vue'
export default {
    name: "Stopwatches",
    props: {
        stopwatches: Array,
    },
    components: {
        Stopwatch,
    },
};
</script>

<style scoped>

</style>