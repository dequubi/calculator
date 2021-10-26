<template>
  <p class="seamNum">Шов {{seam.id}}</p>
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
  margin-top: 5px;
  padding: auto;
}
</style>