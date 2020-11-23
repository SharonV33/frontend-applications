<template>
    <div class="home">
        <homeOverview msg="Mindervaliede parkeer garages"/>
        <pie v-if="chartData" :chartData="chartData" />
        <bar />
        <buttons />
    </div>
</template>

<script>
    // @ is an alias to /src
    import homeOverview from '@/components/homeOverview.vue'
    import buttons from '@/components/buttons.vue'
    import pie from '@/components/pie.vue'
    import bar from '@/components/bar.vue'
    import * as jsonData from'@/helpers/jsonscript.js'
    export default {
        name: 'Home',
        components: {
            homeOverview,
            buttons,
            pie,
            bar
        },
        data () {
            return {
                chartData : []
            }
        },
        mounted () {
            this.fetchData()
        },
        methods: {
            async fetchData () {
                this.chartData = await jsonData.default();
            }
        }
    }
</script>