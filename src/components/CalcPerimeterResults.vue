<template>
    <div v-for="perimeter in perimeters" :key="perimeter.id">
        <div>{{perimeter.id}}</div>
    </div>
</template>

<script>
export default {
    props: {
        perimeters: {
            type: Array,
            default: []
        }
    }
}
</script>

<style>

</style>