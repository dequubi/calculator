<template>
     <div class="table">
        <div v-if="perimeters[0].perimeterType === 'rectangle'" class="row-rectangle">
            <div class="h-cell name">Номер периметра</div>
            <div class="h-cell high">Высота</div>
            <div class="h-cell lenght">Длина</div>
            <div class="h-cell width">Ширина</div>
            <div class="h-cell blocks">Количество блоков</div>
            <div class="h-cell d-picks">Количество алмазных кирок</div>
        </div>
        <div v-if="perimeters[0].perimeterType === 'circle'" class="row-circle">
            <div class="h-cell name">Номер периметра</div>
            <div class="h-cell high">Высота</div>
            <div class="h-cell radius">Радиус</div>
            <div class="h-cell blocks">Количество блоков</div>
            <div class="h-cell d-picks">Количество алмазных кирок</div>
        </div>
        <template v-for="perimeter in perimeters" :key="perimeter.id">
            <div v-if="perimeter.id !== '' && perimeter.lenX !== '' && perimeter.lenY !== ''" class="row-rectangle">
                <div class="cell name">{{perimeter.id}}</div>
                <div class="cell high">64</div>
                <div class="cell lenght">{{perimeter.lenY}}</div>
                <div class="cell width">{{perimeter.lenX}}</div>
                <div class="cell blocks">{{perimeter.lenX * perimeter.lenY * version(perimeter.version)}}</div>
                <div class="cell d-picks">{{Math.ceil((perimeter.lenX * perimeter.lenY * version(perimeter.version)) / 1561)}}</div>
            </div>
            <div v-if="perimeter.perimeterType == 'circle' && perimeter.id !== '' && perimeter.lenX !== ''" class="row-circle">
                <div class="cell name">{{perimeter.id}}</div>
                <div class="cell high">64</div>
                <div class="cell radius">{{perimeter.lenX}}</div>
                <div class="cell blocks">{{Math.ceil(perimeter.lenX * perimeter.lenX * 3.1415 * version(perimeter.version))}}</div>
                <div class="cell d-picks">{{Math.ceil((3.1415 * perimeter.lenX * perimeter.lenX * version(perimeter.version)) / 1561)}}</div>
            </div>
        </template>
    </div>
</template>

<script>
export default {
    props: {
        perimeters: {
            type: Array,
            default: []
        }
    },
    methods: {
        version(vers) {
            if(vers == "17")
                return 64;
            else if (vers == "18")
                return 128;
            else
                return 64;
        }
    }
}
</script>

<style>
.table {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.header, .row-rectangle, .row-circle {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 5px;
}

.row-circle {
    grid-template-columns: repeat(5, 1fr);
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