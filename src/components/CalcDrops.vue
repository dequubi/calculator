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
    <button class="btn" @click="addMob">Добавить моба</button>
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
      this.countMob +=1;
      const newMob = {
        id: this.countMob,
        name: "",
        lootQuantity: ""
      }
      this.mobs.push(newMob);
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

.btn{
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: cornflowerblue;
  color: white;
  border: 1px blue;
  border-radius: 4px;
}

</style>