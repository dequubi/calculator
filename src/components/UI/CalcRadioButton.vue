<template>
  <input
      type="radio"
      :name="$attrs.name"
      :value="$attrs.value"
      v-model="modelValue"
      @change="changeInput">
  <label> {{ $attrs.label }} </label>
</template>

<script>
export default {
  name: "CalcRadioButton",
  props: {
    modelValue: {
      type: String
    }
  },
  methods: {
    changeInput(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }

}
</script>

<style scoped>
label {
  margin-left: 5px;
}
</style>