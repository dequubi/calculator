<template>
<div class="input">
  <div class="label"> {{ $attrs.label }} </div>
  <input :value="modelValue" @input="updateInput">
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
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)

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

</style>