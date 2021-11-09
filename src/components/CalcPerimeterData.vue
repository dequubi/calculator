<template>
  <h3 class="perimeterNum">Периметр {{perimeter.id}}</h3>
  <div class="inputs">
    <calc-input
        label="Длина"
        v-model="perimeter.lenX"
        @input="updateInput"
    />
    <calc-input
        label="Длина"
        v-model="perimeter.lenY"
        @input="updateInput"
    />
    <calc-input
        label="Версия"
        v-model="perimeter.verison"
        @input="updateInput"
    />
  </div>
</template>

<script>
import CalcInput from "./UI/CalcInput";

export default {
  name: "CalcPerimeterData",
  components: {CalcInput},
  props: {
    perimeter: {
      id: 1,
      perimeterType: "",
      lenX: "",
      lenY: "",
      version: ""
    }
  },
  methods: {
    updateInput(event) {
      this.$emit('update:perimeter', event.target.value)
    }
  }
}
</script>

<style scoped>

.perimeterNum{
  margin-top: 10px;
  padding: auto;
}

.inputs {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  justify-content: space-between;
  align-items: end;
}
</style>