<template>
  <div>
    <h2>Выберите фильтры</h2>
    <div class="drop-downs">
      <div class="dd">
        <calc-drop-down
          v-model="dropDownPerimeterType"
          label="Тип периметра"
          :options="dropDownPerimeterTypeOptions"
          @change="updatePerimeterType"/>
      </div>
      <div class="dd">
        <calc-drop-down
          v-model="dropDownGameVersion"
          label="Версия игры"
          :options="dropDownGameVersionOptions"
          @change="updateGameVersion"/>
      </div>
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
      dropDownGameVersion: "",
      dropDownGameVersionOptions: [
        {value: '17', name: '1.17 и ранее'},
        {value: '18', name: '1.18+'}
      ],
      perimeters: [
        {id: 1, perimeterType: "circle", lenX: "", lenY:"", version:"17"},
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
    updateGameVersion(event){
      this.perimeters.forEach(perimeter => {
        perimeter.version = this.dropDownGameVersion
      })
    },
    addPerimeter() {
      this.countPerimeter +=1;
      const newPerimeter = {
        id: this.countPerimeter,
        perimeterType: this.dropDownPerimeterType,
        lenX: "",
        lenY: "",
        version: this.dropDownGameVersion
      }
      this.perimeters.push(newPerimeter);
    }
  }
}
</script>

<style scoped>
.drop-downs {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
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