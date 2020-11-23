<template>
    <h1>pie</h1>
    <svg class="pie"></svg>
    {{ chartData.GR }}
</template>

<script>
     import * as d3 from 'd3';

    export default {
        name: "pie",
        props: ['chartData'],
        data() {
            return {
                svg: Object,
                width: 450,
                height: 450,
                radius: 200
            }
        },
        mounted() {
            this.buildPieChart()

        },
        methods: {
            buildPieChart: function() {
                let data = this.chartData.GR
                this.svg = d3.selectAll(".pie")

                console.log(data)


                this.svg
                    .attr("width", this.width)
                    .attr("height", this.height)


                const g = this.svg.append('g')
                    .attr('transform', `translate(${this.width / 2}, ${this.height / 2})`)

                const color = d3.scaleOrdinal(data)
                    .domain(data)
                    .range(["#98abc5", "#8a89a6"])


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

</style>