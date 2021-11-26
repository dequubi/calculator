<template>
  <div>
    <h2>Введите данные</h2>
    <div class="mob-list">
      <calc-mob-data
        v-for="mob in mobs"
        :mob="mob"
        :key="mob.id"
      />
    </div>
    <div class="buttons">
      <button
        v-if="countMob < 5"
        class="btn"
        @click="addMob">Добавить моба</button>
      <button
        v-if="countMob > 1"
        class="btn-delete"
        @click="deleteMob">Удалить моба</button>
      <button v-if="!isResult"
        class="btn-result"
        @click="showResult">Показть расчеты</button>
      <button v-else
        class="btn-result"
        @click="showResult">Скрыть расчеты</button>
    </div>
    <transition
      name="fade"
      mode="out-in">
      <calc-mob-results
        v-if="isResult"
        :mobs="mobs"/>
    </transition>
  </div>
</template>

<script>

import CalcDropDown from "./UI/CalcDropDown"
import CalcMobData from "./CalcMobData"
import CalcMobResults from "./CalcMobResults"

export default {
  name: "CalcMob",
  components: {CalcMobData, CalcDropDown, CalcMobResults},
  data() {
    return {
      mobs: [
        {id: 1, name: "", lootQuantity: ""},
      ],
      countMob: 1,
      isResult: false
    }
  },
  methods:{
    addMob() {
      if (this.countMob >= 5)
        return;
      this.countMob +=1;
      const newMob = {
        id: this.countMob,
        name: "",
        lootQuantity: ""
      }
      this.mobs.push(newMob);
    },
    deleteMob() {
      if (this.countMob < 1)
        return;
      this.mobs.pop()
      this.countMob--
    },
    showResult() {
      this.isResult = !this.isResult
    }
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.filters {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.btn-result {
  background-color: #a0c864;
  border-color: #b0ff3a;
  margin-left: auto;
}

.btn-result:hover {
  background-color: #81a34e;
}



</style>