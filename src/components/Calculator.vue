<template>
  <h2>1. Выберите вид работ</h2>
  <div class="radio-list">
    <div class="radio" v-for="radio in radioButtons" :key="radio.value">
      <calc-radio-button
          name="work-type"
          :label="radio.label"
          v-model="calc"
          :value="radio.value"/>
    </div>
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


<style>
.radio-list {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
</style>