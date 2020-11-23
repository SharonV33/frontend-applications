<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
    <pie :chartData="chartData" />
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

  async created() {
      async function fetchData() {
        let fetchedData =  await jsonData.default()
        let data = await fetchedData
        return data

      }
    this.chartData = await fetchData()
    return fetchData()
  },

  methods: {
  }

}
</script>

