<template>
  <div class="app">
    <Calculator></Calculator>
  </div>
</template>

<script>
  import Calculator from "@/components/Calculator";

  export default {
    name: "App",

    components: {Calculator},

    data() {
      return {

      }
    }
  }

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', Arial, Helvetica, sans-serif;
}

.app {
  background-image: url("./assets/background.jpg");
  background-position: center;
  height: 100vh;
  background-size: cover;
}

h2 {
  margin: 10px 0;
}

</style>