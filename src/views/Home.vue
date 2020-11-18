<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
    <buttons />
    <pie />
    <bar />
  </div>
</template>

<script>
// @ is an alias to /src
import homeOverview from '@/components/homeOverview.vue'
import buttons from '@/components/buttons.vue'
import pie from '@/components/pie.vue'
import bar from '@/components/bar.vue'

export default {
  name: 'Home',
  components: {
    homeOverview,
    buttons,
    pie,
    bar
  }
}
</script>

