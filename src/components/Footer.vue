<template>
    <div class='footer2'>
        <div class='license zen-font'>
            <p>Copyrights © 2021 Webdev5 - All Right Reserved</p>
        </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+Antique:wght@300&display=swap');

.zen-font {
    font-family: 'Zen Kaku Gothic Antique', sans-serif;
}

.footer2 {
    background-color: 63B4B8;
    box-sizing: border-box;
    display: table;
    width: 100%;
    height: 30px;
    color: white;
    font-size: 15px;
    bottom: 0;
}

.license {
    padding: 20px;
    border-top: 1px solid #ddd;
    text-align: center;
    color: white;
    font-size: 17px;
    margin-top: 40px;
}
</style>