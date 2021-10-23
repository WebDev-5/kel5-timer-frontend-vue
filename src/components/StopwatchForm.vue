<template>
  <form class="text-center">
    <input
      id="title"
      type="text"
      class="baloo-font"
      placeholder="Enter Title for Stopwatch ..."
    />
    <input id="addWatch-btn" type="submit" class="baloo-font" value="ADD" />
    <button id="removeAll_btn">REMOVE ALL</button>
  </form>
  <hr />
</template>

<script>
export default {
  name: "StopwatchForm",
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Allerta+Stencil&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Baloo+Chettan+2&display=swap");

.baloo-font {
  font-family: "Baloo Chettan 2", cursive;
}

.text-center {
  text-align: center;
}

#removeAll_btn {
  font-size: 11px;
  background-color: #d9534f;
  padding: 16px 20px;
  padding-left: -50px;
  text-decoration: none;
  margin: 8px 0;
  cursor: pointer;
  border-radius: 24px;
  border: 4px solid white;
  transition: 0.5s;
}

input[type="text"] {
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

input[type="text"]::placeholder {
  color: white;
}

input[type="text"]:focus {
  border: 4px solid rgb(34, 118, 202);
  background: white;
  color: black;
}

input[type="text"]:focus::placeholder {
  color: black;
}

input[type="submit"] {
  color: white;
  padding: 12px 20px;
  padding-left: -50px;
  text-decoration: none;
  margin: 8px 0;
  cursor: pointer;
  border-radius: 24px;
  border: 4px solid white;
  background: none;
  transition: 0.5s;
}

input[type="submit"]:hover {
  background: white;
  color: #63b4b8;
}

#removeAll_btn{
  font-size: 11px;
  background-color: #d9534f;
  padding: 16px 20px;
  padding-left: -50px;
  text-decoration: none;
  margin: 8px 0;
  cursor: pointer;
  border-radius: 24px;
  border: 4px solid white;
  transition: 0.5s;
}

#removeAll_btn:hover{
  background: white;
  color: #d9534f;
}
</style>
