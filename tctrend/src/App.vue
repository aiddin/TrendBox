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
    // values: [  8.1,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1,8.1, 8.1,8.1, 8.1,8.1,], //15 

    values: [  8.1 ,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1,8.1], //11
    
    // values: [  8.1,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1], //10
    
    // values: [  8.1,8.4,8.4,8.1,8.0],// <10
    up: 'green',
    down: 'red',
    unchanged: 'yellow',
    nullColor:'grey',
  
  };  
}
}

</script>


