<template>
  <div>
    <span>
      <tr v-for="trend in trends" :key="trend.id">
        <span :style="unchangedStyle" v-if="trend.direction === 'unchanged' " class="arrow unchanged"></span>
        <span :style="downStyle" v-if="trend.direction === 'down'" class="arrow arrow-down"></span>
        <span :style="upStyle" v-if="trend.direction === 'up'" class="arrow arrow-up"></span>
        
      </tr>
    </span>
    
  </div>
 
</template>

<script>

export default {
  props: ["values","up","down","unchanged"],
    data() {
    return {
      val: this.values[0],
      compareValue: 0,
      trends: [
      ],
    };
  },
  computed:{
    upStyle() {
      if (this.up === undefined) return "";
      else
        return {
          "border-bottom-color": this.up,
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
          "border-top-color": this.down,
        };
    },
  },
  methods: {
    // Method to check if a value is the same, more or less than the compareValue
      checkValue() {
      for (let i = 0; i < this.values.length; i++) {
        this.compareValue=this.values[i];
        if (this.compareValue === this.val) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'unchanged'})
        } else if (this.compareValue > this.val) {
          this.trends.push({id:i ,values: this.compareValue ,direction :'up'});  
        } else if  (this.compareValue < this.val){
          this.trends.push({id:i ,values: this.compareValue ,direction :'down'});      
        }
        this.val=this.compareValue;
      
      }
        
       console.log(this.trends);
      },
},
beforeMount() {
  this.checkValue();
},
};
</script>

<style>

.arrow{
  text-align: center;
  align-items: center;
  margin: 10px;
  display: inline-flex;
  border: 1vh solid transparent;
}
.arrow.unchanged {
  width: 8vh;
  background: rgb(110, 110, 110);
}
.arrow.arrow-up{
  border: 7vh solid transparent;
  border-bottom-color: green;
  border-top-width: 0px;
}
.arrow.arrow-down{
  border: 7vh solid transparent;
  border-top-color: red;
  border-bottom-width: 0px;
}

</style>