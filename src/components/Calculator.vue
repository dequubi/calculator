<template>
  <h2>Выберите тип калькулятора</h2>
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

import CalcDrops from "@/components/CalcDrops";
import CalcPerimeter from "@/components/CalcPerimeter";
import CalcRadioButton from "./UI/CalcRadioButton";

export default {
  name: "Calculator",

  components: {CalcRadioButton, CalcDrops, CalcPerimeter},

  data() {
    return {
      calc : 'calc-drops',
      radioButtons: [
        {
          label: "Сколько мобов нужно убить, чтобы гарантированно выбить с них X количество лута",
          value: "calc-drops"
        },
        {
          label: "Калькулятор периметра",
          value: "calc-perimeter"
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