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

                //asign size of svg
                svg
                    .attr('width', this.width)
                    .attr('height', this.height)

                //create size of pie chart
                const g = svg.append('g')
                    .attr('transform', `translate(${this.width / 2}, ${this.height / 2})`)

                //create colour scale for slices
                const color = d3.scaleOrdinal(data)
                    .domain(data)
                    .range(['#98abc5', '#8a89a6'])

                //add data each slice of the chart
                const pie = d3.pie()
                    .value(data => data.value)

                //create inner and outer radius of the chart
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
