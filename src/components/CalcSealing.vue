<template>
  <p>2. Настройте фильтры</p>

  <calc-drop-down
      v-model="roadClimateZone"
      :options="roadClimateZoneOptions"
  />


</template>

<script>

import CalcDropDown from "./UI/CalcDropDown";
export default {
  name: "CalcSealing",
  components: {CalcDropDown},
  data() {
    return {
      roadClimateZone : '',
      roadClimateZoneOptions : [
        {value: 'zone1', name: 'zone1'},
        {value: 'zone2', name: 'zone2'},
      ]
    }
  }
}
</script>

<style scoped>

</style>