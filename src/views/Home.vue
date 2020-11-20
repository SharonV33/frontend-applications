<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
    <pie v-bind:data="data" />
    <bar />
    <buttons />
    <button v-on:click="checkData">check json</button>
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
      data: null
    }
  },
  methods: {
    checkData: async function() {
      const fetchedData =  await jsonData.default()
      this.data = fetchedData
    }
  }
}
</script>

