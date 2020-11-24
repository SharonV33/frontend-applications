<template>
    <h1>bar</h1>
    <svg class="bar"></svg>
    <p>data {{ chartData }}</p>
</template>

<script>
    import * as d3 from 'd3';
    import { max } from 'd3'

    export default {
        name: "bar",
        props: {
            chartData: Object
        },
        data() {
            return {
                svg: Object,
                margin: {top: 10, right: 0, bottom: 70, left: 30},
                width: 470,
                height: 320,
            }
        },
        mounted() {
            this.buildBarChart()
        },
        updated() {
            this.buildBarChart()
        },
        methods: {
            buildBarChart: async function() {
                const data = this.chartData

                this.svg = d3.selectAll(".bar")
                const svg = this.svg

                svg
                    .selectAll("*")
                    .remove()

                svg
                    .attr("width", this.width)
                    .attr("height", this.height)

                let xAxis = d3.scaleBand()
                    .range([0, this.width])
                    .domain(data.map(data => data.name))
                    .padding(0.5)

                let yAxix = d3.scaleLinear()
                    .domain([0, max(data, data => data.isDisabled)])
                    .range([this.height, 0])


                //set up size of svg
                svg.attr("width", this.width + this.margin.left + this.margin.right)
                    .attr("height", this.height + this.margin.top + this.margin.bottom)
                    .append("g")
                    .attr("transform",
                        "translate(" + this.margin.left + "," + this.margin.top + ")")


                //set up x axis
                svg.append("g")
                    .attr("class", "xAxis")
                    .attr("transform", "translate(0," + this.height + ")")
                    .call(d3.axisBottom(xAxis))
                    .selectAll("text")
                    .attr("transform", "translate(-10,10)rotate(-90)")
                    .style("text-anchor", "end")


                //set up y axis
                svg.append("g")
                    .attr("class", "yAxis")
                    .call(d3.axisLeft(yAxix))


                svg.selectAll("bar")
                    .data(data)
                    .attr("class", "bar")
                    .enter()
                    .append("rect")
                    .attr("x", function (data) {
                        return xAxis(data.name)
                    })
                    .attr("y", function (data) {
                        return yAxix(data.isDisabled)
                    })
                    .attr("width", xAxis.bandwidth())
                    .attr("height", function (data) {
                        return this.height - yAxix(data.isDisabled)
                    })
                    .attr("fill", "#8A89A6")
            }

        }
    }
</script>

<style scoped>

</style>