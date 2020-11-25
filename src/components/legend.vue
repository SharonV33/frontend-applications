<template>
    <svg class="legend"></svg>
</template>

<script>
    import * as d3 from 'd3';

    export default {
        name: "Legend",
        props: {
            chartData: Object
        },
        data() {
            return {
                svg: Object
            }
        },
        mounted() {
            this.buildLegend()
        },
        updated() {
            this.buildLegend()
        },
        methods: {
            buildLegend: function() {
                console.log(this.chartData)
                this.svg = d3.selectAll(".legend")
            }
        }
    }
</script>

<style scoped>

</style>
