<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :values="values"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
export default {
  name: 'App',
  components: {
    HelloWorld
  },

data() {
  return {
    values: [8.19, 8.09, 8.12, 8.12, 8.42, 8.0, 8.39, 8.5, 8.24, 8.16],
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