<template>
  <div>
    <h2>Введите данные</h2>
    <div class="mob-list">
      <calc-mob
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
    </div>
  </div>
</template>

<script>

import CalcDropDown from "./UI/CalcDropDown";
import CalcMob from "./CalcMob";

export default {
  name: "CalcDrops",
  components: {CalcMob, CalcDropDown},
  data() {
    return {
      mobs: [
        {id: 1, name: "", lootQuantity: ""},
      ],
      countMob: 1
    }
  },
  methods:{
    addMob(){
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
    deleteMob(){
      if (this.countMob < 1)
        return;
      this.mobs.pop()
      this.countMob--
    }

  }
}
</script>

<style scoped>

.filters {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.buttons {
  display: flex;
  gap: 10px;
}

</style>