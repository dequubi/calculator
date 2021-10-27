<template>
  <div>
    <h2>2. Настройте фильтры</h2>
    <div class="filters">
      <div class="dropdown">
        <calc-drop-down
            v-model="roadClimateZone"
            label="Выберите дорожно-климатическую зону"
            :options="roadClimateZoneOptions"
        />
      </div>
      <div class="dropdown">
        <calc-drop-down
            v-model="roadClimateZone"
            label="Выберите герметик"
            :options="roadClimateZoneOptions"
        />
      </div>
    </div>
    <h2>3. Введите данные</h2>
    <div class="seam-list">
      <calc-seam
        v-for="seam in seams"
        :seam="seam"
        :key="seam.id"
      />
    </div>
    <button class="btn" @click="addSeam">Добавить шов</button>
  </div>
</template>

<script>

import CalcDropDown from "./UI/CalcDropDown";
import CalcSeam from "./CalcSeam";

export default {
  name: "CalcSealing",
  components: {CalcSeam, CalcDropDown},
  data() {
    return {
      roadClimateZone : '',
      roadClimateZoneOptions : [
        {value: 'zone1', name: 'zone1'},
        {value: 'zone2', name: 'zone2'},
      ],
      seams: [
        {id: 1, len: "", cuttingWidth: "", depth: ""},
      ],
      countSeam: 1
    }
  },
  methods:{
    addSeam(){
      this.countSeam +=1;
      const newSeam = {
        id: this.countSeam,
        len: "",
        cuttingWidth: "",
        depth:""
      }
      this.seams.push(newSeam);
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