<template>
  <h3 class="mobNum">Моб {{mob.id}}</h3>
  <div class="inputs">
    <div class="dropdown">
        <calc-drop-down
            v-model="mob.name"
            label="Название моба"
            :options="mobTypeOptions"
            :error="mob.nameError"
        />
      </div>
    <calc-input
        label="Количество предметов"
        type="number"
        v-model="mob.lootQuantity"
        @input="updateInput"
        :error="mob.lootError"
    />
  </div>
</template>

<script>
import CalcInput from "./UI/CalcInput";
import CalcDropDown from "./UI/CalcDropDown.vue"

export default {
  name: "CalcMobData",
  components: {CalcInput, CalcDropDown},

  props: {
    mob: {
      id: 1,
      name: "",
      lootQuantity: ""
    }
  },
  methods: {
    updateInput(event) {
      this.$emit('update:mob', event.target.value)
    }
  },
  data() {
    return {
      mobType : '',
      mobTypeOptions : [
        {value: 'Скелет-иссушитель', name: 'Скелет-иссушитель - Череп скелета-иссушителя'},
        {value: 'Эндермен', name: 'Эндермен - Жемчуг края'},
        {value: 'Шалкер', name: 'Шалкер - Панцирь шалкера'},
        {value: 'Ифрит', name: 'Ифрит - Огненный стержень'},
        {value: 'Страж', name: 'Страж - Призмариновый кристалл'},
      ]
    }
  }
}
</script>

<style scoped>

.mobNum{
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