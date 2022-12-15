<template>
  <div id="app">

    <tc-trend :values="values" :down="down" :up="up" :unchanged="unchanged"/>
  </div>
</template>

<script>
import TcTrend from './components/TcTrend.vue'
export default {
  name: 'App',
  components: {
    TcTrend
  },

data() {
  return {
    values: [8.19,8.19, 8.09,8.09, 8.12, 8.12, 8.42,8.42, 8.0, 8.39,8.39,8.39, 8.5, 8.24, 8.24, 8.16],
    up: 'blue',
    down: 'green',
    unchanged: 'purple',
  
  };  
}

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
<!-- 9.34
8.38
8.15
8.84
9.36
8.52
9.40
8.58
8.44
9.51 -->