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
    <button class="btn" @click="addmob">Добавить моба</button>
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
      roadClimateZone : '',
      roadClimateZoneOptions : [
        {value: 'zone1', name: 'zone1'},
        {value: 'zone2', name: 'zone2'},
      ],
      sealantType : '',
      sealantTypeOptions : [
        {value: 'seal1', name: 'seal1'},
        {value: 'seal2', name: 'seal2'},
      ],
      mobs: [
        {id: 1, name: "", lootQuantity: ""},
      ],
      countMob: 1
    }
  },
  methods:{
    addmob(){
      this.countMob +=1;
      const newMob = {
        id: this.countMob,
        len: "",
        cuttingWidth: "",
        depth:""
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