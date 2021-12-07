<template>
  <div> {{ $attrs.label }}</div>
  <select v-model="modelValue" @change="changeOption" :class="{error: $attrs.error}">
    <option disabled value="">Выберите из списка</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CalcDropDown",

  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value);
      this.$emit('change', event.target.value);
    }
  }
}
</script>

<style scoped>
select {
  width: 100%;
}

.error {
  border-color: #ff4f4f;
}
</style>