<template>
  <div>
    <h2>Выберите фильтры</h2>
    <div class="drop-downs">
      <calc-drop-down
        v-model="dropDownPerimeterType"
        label="Тип периметра"
        :options="dropDownPerimeterTypeOptions"
        @change="updatePerimeterType"/>
    </div>
    <h2>Введите данные</h2>
    <div class="perimeter-list">
      <calc-perimeter-data
        v-for="perimeter in perimeters"
        :perimeter="perimeter"
        :key="perimeter.id"
      />
    </div>
    <button class="btn" @click="addPerimeter">Добавить периметр</button>
  </div>
</template>

<script>
import CalcDropDown from './UI/CalcDropDown.vue'
import CalcPerimeterData from './CalcPerimeterData.vue'

export default {
  name: "CalcPerimeter",
  components: {CalcPerimeterData, CalcDropDown},

  data() {
    return {

      dropDownPerimeterType: "",
      dropDownPerimeterTypeOptions: [
        {value: 'circle', name: 'Круглый'},
        {value: 'rectangle', name: 'Прямоугольный'}
      ],

      perimeters: [
        {id: 1, perimeterType: "circle", lenX: "", lenY:"", version:"18"},
      ],
      countPerimeter: 1
    }
  },
  methods:{
    updatePerimeterType(event){
      this.perimeters.forEach(perimeter => {
        perimeter.perimeterType = this.dropDownPerimeterType
      })
    },

    addPerimeter() {
      this.countPerimeter +=1;
      const newPerimeter = {
        id: this.countPerimeter,
        perimeterType: this.dropDownPerimeterType,
        lenX: "",
        lenY: "",
        version: ""
      }
      this.perimeters.push(newPerimeter);
    }
  }
}
</script>

<style scoped>

.btn{
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: cornflowerblue;
  color: white;
  border: 1px blue;
  border-radius: 4px;
}

</style>