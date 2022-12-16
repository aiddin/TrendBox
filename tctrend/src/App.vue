<template>
  <div >

    <tc-trend :values="values" :down="down" :up="up" :unchanged="unchanged" :nullColor="nullColor" />
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
    values: [  8.01,8.16,8.4,8.4,8.1,8.10, 8.19, 8.19, 8.19, 8.19],
    
    up: 'green',
    down: 'red',
    unchanged: 'greenyellow',
    nullColor:'grey',
  
  };  
}
}

</script>


