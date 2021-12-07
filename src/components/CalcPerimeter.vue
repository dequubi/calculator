<template>
  <div>
    <div class="inputs" v-if="!isResult">
      <h2>Выберите фильтры</h2>
      <div class="drop-downs">
        <div class="dd">
          <calc-drop-down
            v-model="dropDownPerimeterType"
            label="Тип периметра"
            :options="dropDownPerimeterTypeOptions"
            @change="updatePerimeterType"
            :error="perimeters[0].typeError"/>
        </div>
        <div class="dd">
          <calc-drop-down
            v-model="dropDownGameVersion"
            label="Версия игры"
            :options="dropDownGameVersionOptions"
            @change="updateGameVersion"
            :error="perimeters[0].versionError"/>
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
      <div class="buttons">
        <button
          v-if="countPerimeter < 5"
          class="btn"
          @click="addPerimeter">Добавить периметр</button>
        <button
          v-if="countPerimeter > 1"
          class="btn-delete"
          @click="deletePerimeter">Удалить периметр</button>
        <button
          class="btn-result"
          @click="showResult">Рассчитать</button>
      </div>
    </div>
    <div class="results"
        v-if="isResult">
      <h2>Результаты</h2>
      <calc-perimeter-results
        :perimeters="perimeters"/>
      <div class="buttons">
        <button
          class="btn-change"
          @click="showResult">
          <div class="arrow">&#5176;</div>
          <div class="text">Изменить расчеты</div>
        </button>
        <button
          class="btn-result"
          @click="newCalc">
          <div class="text">Новый расчёт</div>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import CalcDropDown from './UI/CalcDropDown.vue'
import CalcPerimeterData from './CalcPerimeterData.vue'
import CalcPerimeterResults from "./CalcPerimeterResults.vue"

export default {
  name: "CalcPerimeter",
  components: {CalcPerimeterData, CalcDropDown, CalcPerimeterResults},

  data() {
    return {
      dropDownPerimeterType: "",
      dropDownPerimeterTypeOptions: [
        {value: 'rectangle', name: 'Прямоугольный'},
        {value: 'circle', name: 'Круглый'}
      ],
      dropDownGameVersion: "",
      dropDownGameVersionOptions: [
        {value: '17', name: '1.17 и ранее'},
        {value: '18', name: '1.18+'}
      ],
      perimeters: [
        {id: 1, perimeterType: "rectangle", lenX: "", lenY:"", version:"17"},
      ],
      countPerimeter: 1,
      isResult: false
    }
  },
  methods:{
    updatePerimeterType(event){
      this.perimeters.forEach(perimeter => {
        perimeter.perimeterType = this.dropDownPerimeterType
        if (this.dropDownPerimeterType === "circle")
          perimeter.lenY = ""
      })
    },
    updateGameVersion(event){
      this.perimeters.forEach(perimeter => {
        perimeter.version = this.dropDownGameVersion
      })
    },
    addPerimeter() {
      if (this.countPerimeter >= 5)
        return;
      this.countPerimeter +=1;
      const newPerimeter = {
        id: this.countPerimeter,
        perimeterType: this.dropDownPerimeterType,
        lenX: "",
        lenY: "",
        version: this.dropDownGameVersion
      }
      this.perimeters.push(newPerimeter);
    },
    deletePerimeter(){
      if (this.countPerimeter < 1)
        return;
      this.perimeters.pop()
      this.countPerimeter--
    },
    showResult() {
      let flag = false
      this.perimeters.forEach((perim, index) => {
        perim.xError = perim.lenX === ''
        if (perim.perimeterType == "rectangle") {
          perim.yError = perim.lenY === ''
          if (perim.xError || perim.yError)
            flag = true
        } else {
          if (perim.xError)
            flag = true
        }
      })

      this.perimeters[0].typeError = this.dropDownPerimeterType == ''
      this.perimeters[0].versionError = this.dropDownGameVersion == ''
      if (this.perimeters[0].typeError || this.perimeters[0].versionError)
        flag = true
      if (flag) return

      this.isResult = !this.isResult
      this.$emit('hideInput', this.isResult)
    },
    newCalc() {
      this.countPerimeter = 1
      this.dropDownPerimeterType = ""
      this.dropDownGameVersion = ""
      this.perimeters = [{id: 1, perimeterType: "rectangle", lenX: "", lenY:"", version:"17"}]
      this.isResult = !this.isResult
      this.$emit('hideInput', this.isResult)
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

.buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.btn-result {
  background-color: #a0c864;
  border-color: #b0ff3a;
  margin-left: auto;

}

.btn-change {
  margin-left: 0;
  display: flex;
  gap: 5px;
  align-items: center;
}

.arrow {
  font-weight: 700;
}

.btn-result:hover {
  background-color: #81a34e;
}

</style>