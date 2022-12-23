<template>
  <div >

    <tc-trend-bar :values="values" :down="down" :up="up" :unchanged="unchanged" :nullColor="nullColor" />
  </div>
  
</template>

<script>
import TcTrendBar from './components/TcTrendBar.vue'
export default {
  name: 'App',
  components: {
    TcTrendBar
  },

data() {
  return {
   
    values:this.changeValue(), //values to be passed to tc-trend
    up: 'green',
    down: 'red',
    unchanged: 'yellow',
    nullColor:'grey',
  
  };  

},
methods: {
  setValues(){
    this.values=this.changeValue();
  },  
  changeValue() {
    return [  8.1,8.4,8.4,8.1,8.0];
    

      
    
    
  },
  },
mounted() {
  this.setValues();
  setInterval(() => {
   this.values.push((8 + Math.random()).toFixed(1));
  
}, 2000);

}
}
</script>


