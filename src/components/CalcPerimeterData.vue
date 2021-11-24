<template>
  <h3 class="perimeterNum">Периметр {{perimeter.id}}</h3>
  <div>
    <calc-input
      v-if="perimeter.perimeterType === 'circle'"
      class="single-input"
      label="Радиус"
      type="number"
      v-model="perimeter.lenX"
      @input="updateInput"
    />
    <div v-else class="inputs">
      <calc-input
          label="Длина"
          type="number"
          v-model="perimeter.lenX"
          @input="updateInput"
      />
      <calc-input
          label="Ширина"
          type="number"
          v-model="perimeter.lenY"
          @input="updateInput"
      />
    </div>
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

.single-input {
  display: grid;
  grid-template-columns: 1fr;
  justify-content: space-between;
  align-items: end;
}

.inputs {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  justify-content: space-between;
  align-items: end;
}
</style>