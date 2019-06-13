<template>
  <div id="app">
    <!-- <base-label></base-label> -->
    <base-event></base-event>
    <base-canvas-one></base-canvas-one>
    <base-canvas-two></base-canvas-two>
  </div>
</template>

<script>
import baseLabel from '../components/base-label'
import baseEvent from '../components/base-event'
import baseCanvasOne from '../components/base-canvas-one'
import baseCanvasTwo from '../components/base-canvas-two'
export default {
  name: 'app',
  components:{
    baseLabel,
    baseEvent,
    baseCanvasOne,
    baseCanvasTwo
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
</style>
