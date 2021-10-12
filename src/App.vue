<template>
  <div class="app">
    <input type="radio" value="calc-seam" v-model="calc">
    <label>Герметизация швов</label>
    <br>
    <input type="radio" value="calc-rubble" v-model="calc">
    <label>Устройство ЩМДШ</label>
    <br>
    <input type="radio" value="calc-protection" v-model="calc">
    <label>Защита и восстановление покрытия</label>
    <br>
    <component
        :is="calc"
    />
  </div>
</template>

<script>
import CalcRubble from "@/components/CalcRubble";
import CalcSeam from "@/components/CalcSeam";
import CalcProtection from "@/components/CalcProtection";

export default {
  components: {CalcProtection, CalcSeam, CalcRubble},

  data() {
    return {
      calc : ''
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