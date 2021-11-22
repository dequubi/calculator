<template>
<div class="input">
  <div class="label"> {{ $attrs.label }} </div>
  <input
    :value="modelValue"
    @input="updateInput"
    :type="$attrs.type"
    @keydown="dotCheck"
    pattern="[0-9]">
  <div v-if="$attrs.error != ''"> {{ $attrs.error }} </div>
</div>
</template>

<script>
export default {
  name: "CalcInput",

  props: {
    modelValue: ""
  },
  methods: {
    updateInput(e) {
      if (e.target.value.length != 0)
        e.target.value = parseInt(e.target.value)
      this.$emit('update:modelValue', e.target.value)
    },
    dotCheck(e) {
      if (e.key === '.')
        e.preventDefault()
      if (e.target.value.length == 0 && e.key === '0')
        e.preventDefault()
    }
  }
}
</script>

<style scoped>

.label {
  font-size: smaller;
}

input {
  width: 100%;
}

input:invalid:focus {
  /* outline: none !important; */
  border: 2px solid #ce6161;
  background-color: #ffc3c3;
}

input:invalid {
  border: 2px solid #ce6161;
  background-color: #ffc3c3;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  display: none;
  margin: 0;
}

</style>