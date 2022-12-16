<template>
    <div>
      <th v-for="trends in trends" :key="trends" >
        <td :style="unchangedStyle" v-if="trends.direction === 'unchanged' " class="box unchanged"></td>
        <td :style="downStyle" v-if="trends.direction === 'down'" class="box down"></td>
        <td :style="upStyle" v-if="trends.direction === 'up'" class="box up"></td>
        <td  :style="nullStyle" v-if="trends.direction === 'null'" class="box null"></td>
      </th>
  </div>
  {{values}}
</template>
<script>
//normal box lol just box  of array with colors
export default {
  props: ["values","up","down","unchanged","nullColor"],
    data() {
    return {
      limitarr:this.limit,
     
      compareValue: 0,
      trends: [
      ],
      valuesarr: this.values.map((item) => {
        return item;
      }), 
    };
  },
  computed:{
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
      // }
      // else if (this.valuesarr.length >10){
      //   this.valuesarr.splice(0,(this.values.length-10));
      // }
      for (let i = 0; i < 10; i++) {
        this.compareValue=this.valuesarr[i];
        const valuesa = this.valuesarr[i-1];
        if (this.compareValue === undefined){
          this.trends.push({id:i ,values: this.compareValue ,direction :'null'});
        }
        else if (this.compareValue === valuesa) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'unchanged'})
        } else if (this.compareValue > valuesa) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'up'});  
        } else if  (this.compareValue < valuesa){
          this.trends.push({id:i ,values: this.compareValue ,direction :'down'});
        }
        this.val=this.compareValue;
        console.log("hehe")
      }
      if (this.trends.length >10){
        this.trends.splice(0,(this.trends.length-10));
      
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