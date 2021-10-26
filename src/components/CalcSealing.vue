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
    <calc-seams-list
      v-model="seams"
      :seams="seams"
    />
  </div>
</template>

<script>

import CalcDropDown from "./UI/CalcDropDown";
import CalcSeam from "./CalcSeam";
import CalcSeamsList from "./CalcSeamsList";

export default {
  name: "CalcSealing",
  components: {CalcSeamsList, CalcSeam, CalcDropDown},
  data() {
    return {
      roadClimateZone : '',
      roadClimateZoneOptions : [
        {value: 'zone1', name: 'zone1'},
        {value: 'zone2', name: 'zone2'},
      ],
      seams: [
        {id: 0, len: "", cuttingWidth: "", depth: ""},
      ]
    }
  }
}
</script>

<style scoped>

</style>