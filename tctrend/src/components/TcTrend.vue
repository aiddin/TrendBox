<template>
    <div>
      <th v-for="trends in trends" :key="trends" >
        <td :style="unchangedStyle" v-if="trends.direction === 'unchanged' " class="box unchanged"></td>
        <td :style="downStyle" v-if="trends.direction === 'down'" class="box down"></td>
        <td :style="upStyle" v-if="trends.direction === 'up'" class="box up"></td>
        <td  :style="nullStyle" v-if="trends.direction === 'null'" class="box null"></td>
      </th>
  </div>
  <!-- {{values}}
  {{trends}} -->
</template>
<script>
//normal box lol just box  of array with colors
export default {
  props: ["values","up","down","unchanged","nullColor"],
    data() {
    return {
      limitarr:this.limit,
      val: this.values[0],
      compareValue: 0,
      trends: [
      ],
      valuesarr: this.values.map((item) => {
        return item;
      }), 
    };
  },
  computed:{
    //styles for the boxes
    upStyle() { 
      if (this.up === undefined) return "";
      else
        return {
          "background-color": this.up,
        };
    },
    unchangedStyle() {
      if (this.unchanged === undefined) return "";
      else
        return {
          "background-color": this.unchanged,
        };
    },
    downStyle() {
      if (this.down === undefined) return "";
      else
        return {
          "background-color": this.down,
        };
    },
    nullStyle() {
      if (this.nullColor === undefined) return "";
      else
        return {
          "background-color": this.nullColor,
        };
    },
  },
  methods: {
    // Method to check if a value is the same, more or less than the compareValue
      checkValue() {
      if (this.values.length <10){
        for(let i=0 ;i< 10-this.values.length;i++ ){
          this.valuesarr.unshift(undefined);
      
        } 
      }
      
      else if (this.valuesarr.length >10){
        this.valuesarr.splice(0,(this.values.length-10));
      }
      for (let i = 0; i < 10; i++) {
        this.compareValue=this.valuesarr[i];
    
        if (this.compareValue === undefined){
          this.trends.push({id:i ,values: this.compareValue ,direction :'null'});
        }
        else if (this.compareValue === this.val) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'unchanged'})
        } else if (this.compareValue > this.val) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'up'});  
        } else if  (this.compareValue < this.val){
          this.trends.push({id:i ,values: this.compareValue ,direction :'down'});
        }
        this.val =this.compareValue;
        console.log("hehe")
      }
      // check this.trends.length and add or remove elements
      if (this.trends.length <10){
        for(let i=0 ;i< 10-this.trends.length;i++ ){
          this.trends.unshift({id:-i ,values: undefined ,direction :'null'});
      
        } 
      }
        else if (this.trends.length >10){
        this.trends.splice(0,(this.trends.length-10));
      }
      else if (this.values.length === 10){
        this.trends.splice(0,1);
        this.trends.unshift({id:0 ,values: undefined ,direction :'null'});
      }
      
      
      console.log("hehe")
},
  },
beforeMount() {
  this.checkValue();
},
};
</script>

<style>

.box {
  box-sizing: border-box;
  width: 3vh;
  height: 5vh;
  background-color: lightgray;
  border: 1px solid rgb(0, 0, 0);
  display: inline-block;
  margin: 0px;
}
.box.up{
  background-color: rgb(241, 31, 31);
}
.box.down{
  background-color: rgb(48, 41, 41);
}
.box.unchanged{
  background-color: rgb(39, 61, 187);
}
.box.null{
  background-color: rgb(39, 61, 187);
}

</style>