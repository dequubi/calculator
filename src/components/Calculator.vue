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

.btn, .btn-delete, .btn-result {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: cornflowerblue;
  color: white;
  border: 1px blue;
  border-radius: 4px;
  cursor: pointer;
}

.btn:hover, .btn-delete:hover {
  background: rgb(73, 112, 185);
}

.btn-delete {
  background: #ed6476;
  color: #000000;
  border: 1px #ff0000;
}

.btn-delete:hover {
  background: #ad3f4e;
}
</style>