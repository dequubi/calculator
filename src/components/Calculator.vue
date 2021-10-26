<template>
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
</template>

<script>

import CalcSeam from "@/components/CalcSeam";
import CalcRubble from "@/components/CalcRubble";
import CalcProtection from "@/components/CalcProtection";

export default {
  name: "Calculator",

  components: {CalcSeam, CalcRubble, CalcProtection},

  data() {
    return {
      calc : 'calc-seam'
    }
  }
}
</script>


<style scoped>

</style>