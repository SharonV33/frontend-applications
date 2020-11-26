<template>
    <svg class="pie"></svg>
    <MyLegend v-bind:chartData="data" />
</template>

<script>
     import * as d3 from 'd3'
     import MyLegend from '@/components/legend'

    export default {
        name: 'pie',
        components: {MyLegend},
        props: {
            chartData: Object
        },
        Components: {
            MyLegend
        },
        data() {
            return {
                svg: Object,
                width: 450,
                height: 450,
                radius: 200,
                data: this.chartData,
            }
        },
        mounted() {
            this.buildPieChart()
        },
        updated() {
            this.buildPieChart()
        },
        methods: {
            buildPieChart: function() {
                const data = this.chartData

                this.svg = d3.selectAll('.pie')
                const svg = this.svg

                svg
                    .selectAll('*')
                    .remove()

                svg
                    .attr('width', this.width)
                    .attr('height', this.height)


                const g = svg.append('g')
                    .attr('transform', `translate(${this.width / 2}, ${this.height / 2})`)

                const color = d3.scaleOrdinal(data)
                    .domain(data)
                    .range(['#98abc5', '#8a89a6'])

                const pie = d3.pie()
                    .value(data => data.value)

                const path = d3.arc()
                    .outerRadius(this.radius)
                    .innerRadius(0)

                const pies = g.selectAll('.arc')
                    .data(pie(data))
                    .enter()
                    .append('g')
                    .attr('class', 'arc')

                pies
                    .append('path')
                    .attr('d', path)
                    .attr('fill', data => color(data.value))


            }
        },
    }
</script>

<style scoped>
    .tooltip {
        position: absolute;
        text-align: center;
        width: 60px;
        height: 28px;
        padding: 2px;
        font: 12px sans-serif;
        background: lightsteelblue;
        border: 0px;
        border-radius: 8px;
        pointer-events: none;
    }
</style>
