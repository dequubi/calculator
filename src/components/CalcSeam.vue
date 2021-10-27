<template>
  <h3 class="seamNum">Шов {{seam.id}}</h3>
  <div class="inputs">
    <calc-input
        label="Длина шва, м"
        v-model="seam.len"
        @input="this.$emit('update:seam.len', value)"
    />
    <calc-input
        label="Ширина разделки шва, мм"
        v-model="seam.cuttingWidth"
        @input="updateInput"
    />
    <calc-input
        label="Глубина заливики камеры шва герметиком, мм"
        v-model="seam.depth"
        @input="updateInput"
    />
  </div>
</template>

<script>
import CalcInput from "./UI/CalcInput";

export default {
  name: "CalcSeam",
  components: {CalcInput},

  props: {
    seam: {
      id: 1,
      len: "",
      cuttingWidth: "",
      depth: ""
    }
  },
  methods: {
    updateInput(event) {
      this.$emit('update:seam', event.target.value)
    }
  }
}
</script>

<style scoped>

.seamNum{
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