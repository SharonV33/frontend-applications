<template>
    <svg class="bar"></svg>
</template>

<script>
    import * as d3 from 'd3'
    import { max } from 'd3'

    export default {
        name: 'bar',
        props: {
            chartData: Object
        },
        mounted() {
            this.buildBarChart()
        },
        methods: {
            buildBarChart: function() {
                const data = this.chartData
                const margin = {top: 10, right: 0, bottom: 70, left: 30}
                const width = 500 - margin.left - margin.right
                const height = 400 - margin.top - margin.bottom

                this.svg = d3.selectAll('.bar')
                const svg = this.svg

                let xAxis = d3.scaleBand()
                    .range([0, width])
                    .domain(data.map(data => data.name))
                    .padding(0.5)

                let yAxix = d3.scaleLinear()
                    .domain([0, max(data, data => data.isDisabled)])
                    .range([height, 0])


                //set up size of svg
                svg.attr("width", width + margin.left + margin.right)
                    .attr("height", height + margin.top + margin.bottom)
                    .append("g")
                    .attr("transform",
                        "translate(" + margin.left + "," + margin.top + ")")


                 //set up x axis
                    svg.append('g')
                    .attr('class', 'xAxis')
                    .attr('transform', 'translate(0,' + height + ')')
                    .call(d3.axisBottom(xAxis))
                    .selectAll('text')
                    .attr('transform', 'translate(-10,10)rotate(-90)')
                    .style('text-anchor', 'end')


                    //set up y axis
                    svg.append("g")
                        .attr("class", "yAxis")
                        .call(d3.axisLeft(yAxix))


                    svg.selectAll('bar')
                        .data(data)
                        .attr('class', 'bar')
                        .enter()
                        .append('rect')
                        .attr('x', function (data) {
                            return xAxis(data.name)
                        })
                        .attr('y', function (data) {
                            return yAxix(data.isDisabled)
                        })
                        .attr('width', xAxis.bandwidth())
                        .attr('height', function (data) {
                            return height - yAxix(data.isDisabled)
                        })
                        .attr('fill', '#8A89A6')
            }

        }
    }
</script>
<style scoped>
    .bar {
        overflow: visible;
        margin-left: 3em;
    }
</style>