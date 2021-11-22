<template>
  <div class="cont">
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
    <transition
      name="fade"
      mode="out-in">
      <component
          :is="calc"
      />
    </transition>
  </div>
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
.cont {
  padding: 20px;
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  width: 720px;
  background-color: white;
  height: 100vh;
}

.radio-list {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>