<template>
  <div>
    <p>2. Настройте фильтры</p>
    <calc-drop-down
        v-model="roadClimateZone"
        label="Label 1"
        :options="roadClimateZoneOptions"
    />
    <calc-drop-down
        v-model="roadClimateZone"
        label="Label 2"
        :options="roadClimateZoneOptions"
    />
    <p>3. Введите данные</p>
    <calc-seam
      v-for="seam in seams"
      :seam="seam"
      :key="seam.id"
    />
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