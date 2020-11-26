<template>
    <section>
        <svg class="legend"></svg>
    </section>
</template>

<script>
    import * as d3 from 'd3'

    export default {
        name: 'MyLegend',
        props: {
            chartData: Object
        },
        mounted() {
            this.buildLegend()
        },
        updated() {
            this.buildLegend()
        },
        methods: {
            buildLegend: function() {
                const svg = d3.selectAll('.legend')
                const size = 20
                const data = this.chartData

                const color = d3.scaleOrdinal()
                    .domain(data)
                    .range(['#98abc5', '#8a89a6'])

                svg.attr('width', 150)
                    .attr('height', 100)
                    .style('border', '1px solid darkgray')

                // Add one dot in the legend for each name.
                svg.selectAll('color')
                    .data(data)
                    .enter()
                    //rect is a default d3 shape
                    .append('rect')
                    .attr('x', 25)
                    .attr('y', function(d,i){ return 25 + i*(size+5)}) // 100 is where the first dot appears. 25 is the distance between dots
                    .attr('width', size)
                    .attr('height', size)
                    .style('fill', data => color(data.name))
                    .text(function(data){ return data.value})

                // Add text label to coloured dots
                svg.selectAll('label')
                    .data(data)
                    .enter()
                    .append('text')
                    .attr('x', 25 + size*1.5)
                    .attr('y', function(d,i){ return 25 + i*(size+5) + (size/2)}) // 100 is where the first dot appears. 25 is the distance between dots
                    .text(function(data){ return data.name})

            }
        }
    }
</script>

<style scoped>

</style>