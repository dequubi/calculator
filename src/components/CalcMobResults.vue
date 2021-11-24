<template>
    <div class="table">
        <div class="header">
            <div class="h-cell name">Название моба</div>
            <div class="h-cell quantity">Количество предметов</div>
            <div class="h-cell 50-p">~50%</div>
            <div class="h-cell 75-p">~75%</div>
            <div class="h-cell 90-p">~90%</div>
            <div class="h-cell 100-p">~100%</div>
        </div>
        <div v-for="mob in mobs" :key="mob.id">
            <div v-if="mob.name !== '' && mob.lootQuantity !== ''" class="row">
                <div class="cell name">{{mob.name}}</div>
                <div class="cell quantity">{{mob.lootQuantity}}</div>
                <div v-for="per in calculatePercentages(mob)" :key="per.name">
                    <div :class="'cell ' + per.name">{{per.val}}</div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        mobs: {
            type: Array,
            default: []
        }
    },
    data() {
        return {

        }
    },
    methods: {
        calculatePercentages(mob) {
            let p, p50, p75, p90, p100

            switch (mob.name) {
                case 'Скелет-иссушитель':
                    p = 0.025
                    break
                case 'Эндермен':
                    p = 0.5
                    break
                case 'Шалкер':
                    p = 0.5
                    break
                case 'Ифрит':
                    p = 0.5
                    break
                case 'Страж':
                    p = 0.6
                    break
                default:
                    break
            }

            p100 = Number(mob.lootQuantity) * this.trials(p, 0.99)
            p90 = Number(mob.lootQuantity) * this.trials(p, 0.90)
            p75 = Number(mob.lootQuantity) * this.trials(p, 0.75)
            p50 = Number(mob.lootQuantity) * this.trials(p, 0.50)

            return [
                {name: "fifty", val: p50},
                {name: "seventy-five", val: p75},
                {name: "ninty", val: p90},
                {name: "hundred", val: p100},
            ]

        },
        trials(p, n) {
            return Math.ceil(Math.log(1.0 - n) / Math.log(1.0 - p));
        }
    },

}
</script>

<style scoped>
.table {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.header, .row {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 5px;
}

.h-cell, .cell {
    padding: 5px;
    text-align: center;
    display: grid;
    place-items: center;
    background-color: #c7c7c7;
    height: 100%;
    border-radius: 3px;
}

.cell {
    background-color: #f3f3f3;
}
</style>