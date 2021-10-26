<template>
  <p>1. Выберите вид работ</p>
  <input type="radio" value="calc-sealing" v-model="calc">
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

import CalcSealing from "@/components/CalcSealing";
import CalcRubble from "@/components/CalcRubble";
import CalcProtection from "@/components/CalcProtection";

export default {
  name: "Calculator",

  components: {CalcSealing, CalcRubble, CalcProtection},

  data() {
    return {
      calc : 'calc-seam'
    }
  }
}
</script>


<style scoped>

</style>