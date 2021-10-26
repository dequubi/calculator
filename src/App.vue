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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>