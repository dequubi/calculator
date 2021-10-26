<template>
  <div> {{ $attrs.label }} </div>
  <input :value="modelValue" @input="updateInput">
  <div v-if="$attrs.error != ''"> {{ $attrs.error }} </div>
</template>

<script>
export default {
  name: "CalcInput",

  props: {
    modelValue: ""
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)

    }
  }
}
</script>

<style scoped>

</style>