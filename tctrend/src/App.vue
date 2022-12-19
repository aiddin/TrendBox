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
   
    var counter= Math.floor(Math.random() * 4) + 1;
    if(counter===1){
     return [  8.1,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1,8.1, 8.1,8.1, 8.1,8.1,];
    }
    else if(counter===2){
      return [  8.1 ,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1,8.1];
    }
    else if(counter===3){
      return [  8.1,8.16,8.16,8.01,8.16,8.4,8.4,8.1,8.0,8.1];
    }
    else if(counter===4){
      
      return [  8.1,8.4,8.4,8.1,8.0];
    }

      
    
    
  },
  },
mounted() {
  setInterval(() => {
    this.setValues();
}, 2000);

}
}
</script>


