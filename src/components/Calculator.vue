<template>
  <p>1. Выберите вид работ</p>
  <div v-for="radio in radioButtons">
    <calc-radio-button
        name="work-type"
        :label="radio.label"
        v-model="calc"
        :value="radio.value"/>
  </div>
  <component
      :is="calc"
  />
</template>

<script>

import CalcSealing from "@/components/CalcSealing";
import CalcRubble from "@/components/CalcRubble";
import CalcProtection from "@/components/CalcProtection";
import CalcRadioButton from "./UI/CalcRadioButton";

export default {
  name: "Calculator",

  components: {CalcRadioButton, CalcSealing, CalcRubble, CalcProtection},

  data() {
    return {
      calc : 'calc-sealing',
      radioButtons: [
        {
          label: "Герметизация швов",
          value: "calc-sealing"
        },
        {
          label: "Устройство ЩМДШ",
          value: "calc-rubble"
        },
        {
          label: "Защита и восстановление покрытия",
          value: "calc-protection"
        }
      ]
    }
  }
}
</script>


<style scoped>

</style>