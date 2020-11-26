<template>
  <h1>Mindervaliede parkeer garages</h1>
  <div class="home">
    <buttons :currentProvince="currentProvince" v-on:change-province="updateProvince($event)"/>
    <section v-if="currentProvince === 'allProvinces'">
      <bar v-if="chartData.[currentProvince]" :chartData="chartData.[currentProvince]"/>
    </section>
    <section v-else>
      <pie v-if="chartData.[currentProvince]" :chartData="chartData.[currentProvince]" />
      <span v-else>intro over visualisatie hier</span>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import buttons from '@/components/buttons.vue'
import pie from '@/components/pie.vue'
import bar from '@/components/bar.vue'
import jsonScript from'@/helpers/jsonscript.js'

export default {
    name: 'Home',
    components: {
        buttons,
        pie,
        bar
    },
    data () {
      return {
        chartData: [],
        currentProvince: '',
      }
    },
    created () {
      this.fetchData()
      if(localStorage.currentProvince) {
        this.currentProvince = localStorage.getItem('currentProvince')
      }
    },
    watch: {
      currentProvince(newProvince) {
        localStorage.setItem('currentProvince', newProvince)
      }
    },
    methods: {
        async fetchData () {
            const data = await jsonScript.fetchData()
            this.chartData = data
        },
        updateProvince: function(newProvince){
          this.currentProvince = newProvince
        }
    }
}
</script>
<style scoped>
  .home {
    display: grid;
    grid-auto-flow: column;
    grid-template-columns: 40% auto;
  }
</style>
