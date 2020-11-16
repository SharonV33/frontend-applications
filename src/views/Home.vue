<template>
  <div class="home">
    <homeOverview msg="Mindervaliede parkeer garages"/>
  </div>
</template>

<script>
// @ is an alias to /src
import homeOverview from '@/components/homeOverview.vue'

export default {
  name: 'Home',
  components: {
    homeOverview
  }
}
</script>

