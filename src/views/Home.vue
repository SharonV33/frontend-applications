<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
    <section v-if="currentProvince === 'allProvinces'">
      <bar :chartData="chartData.[currentProvince]"/>
    </section>
    <section v-else>
      <pie v-if="chartData.[currentProvince]" :chartData="chartData.[currentProvince]" />
      <span v-else>Grafiek wordt geladen...</span>
    </section>

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
        currentProvince: "",
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
          console.log(this.currentProvince)
        },
    }
}
</script>
