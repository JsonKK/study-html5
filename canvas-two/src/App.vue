<template>
  <div id="app">
    <!-- <basic></basic> -->
    <!-- <clock></clock> -->
    <!-- <ball></ball> -->
    <rectangle></rectangle>
  </div>
</template>

<script>
import basic from '../components/basic'
import clock from '../components/clock'
import ball from '../components/ball'
import rectangle from '../components/rectangle'
export default {
  name: 'app',
  components:{
    basic,
    clock,
    ball,
    rectangle
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
