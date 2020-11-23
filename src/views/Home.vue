<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
    <pie v-if="chartData[currentProvince].length" :chartData="chartData" :currentProvince="currentProvince" />
    <span v-else>Grafiek wordt geladen...</span>
    <bar />
    <buttons :currentProvince="currentProvince" v-on:change-province="updateProvince($event)"/>
  </div>
</template>

<script>
// @ is an alias to /src
import homeOverview from '@/components/homeOverview.vue'
import buttons from '@/components/buttons.vue'
import pie from '@/components/pie.vue'
import bar from '@/components/bar.vue'
import jsonScript from'@/helpers/jsonscript.js'

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
        chartData: [],
        currentProvince: "GR",
      }
    },

    mounted () {
      this.fetchData()
    },

    methods: {
        async fetchData () {
            const data = await jsonScript.fetchData()
            this.chartData = data
        },

        updateProvince: function(newProvince){
          this.currentProvince = newProvince
        },
    }
}
</script>
