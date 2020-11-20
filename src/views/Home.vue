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
  data: function(){
    return checkData()
  },
  methods: {
    checkData: async function(){
      const res = await jsonData.default()
      return res
    }
  }

}
</script>

