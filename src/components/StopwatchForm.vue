<template>
<div class="navbar">
  <button 
    id="button-add" 
    type="button" 
    class="zen-font thick-font"  
    @click="addstopwatch">ADD NEW STOPWATCH
  </button>
</div>
<hr>

</template>

<script>
export default {
  name: "StopwatchForm",
};
</script>

<style>
.navbar {
  padding-bottom: 1%;
}

.thick-font {
  font-weight: bold;
}

button[type="button"] {
    color: black;
    padding: 12px 20px;
    padding-left: -50px;
    cursor: pointer;
    border-radius: 20px;
    border: none;
    position: relative;
    display: block;
    transition: 0.5s;
}

button[type="button"]:hover {
    background-color: #DA0037;
    color: white;
}

#button-add {
    font-size: 15px;
    background: #DA0037;
    margin: 0 auto;
    text-align: center;
    color: #FFFFFF;
}
</style>
