<template>
  <div v-if="seams.length > 0">
    <calc-seam
        v-for="seam in seams"
        :seam="seam"
        :key="seam.id"

    />
  </div>
</template>

<script>
import CalcSeam from "./CalcSeam";
export default {
  name: "CalcSeamsList",
  components: {CalcSeam},
  props: {
    seams: {
      required: true
    }
  }

}
</script>

<style scoped>


</style>