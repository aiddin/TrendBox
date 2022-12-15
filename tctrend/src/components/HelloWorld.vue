<template>
  <div>
    <span v-for="trend in trends" :key="trend.id">
      <span v-if="trend.direction === 'up'" class="arrow-up"></span>
      <span v-if="trend.direction === 'down'" class="arrow-down"></span>
      <span v-if="trend.direction === 'unchanged' " class="unchanged"></span>
    </span>
  </div>
  <div><ul>
    <li v-for="value in values" :key="value">
      The value is {{ checkValue(value) }} than {{ compareValue }}
    </li>
  </ul></div>
</template>

<script>
export default {
  data() {
    return {
      values: [5, 10, 15, 20],
    // Define the value to compare against
    
      trends: [
     

      ],
    };
  },
  methods: {
    // Method to check if a value is the same, more or less than the compareValue
      checkValue(value) {
      
        if (value == this.val) {
          this.trends.push({values: value ,direction :'dash'})
          this.val=value;
        } else if (value > this.val) {
          this.trends.push({values: value ,direction :'up'});
          this.val=value;
        } else if  (value < this.val){
          this.trends.push({values: value ,direction :'down'});
          this.val=value;
        }
       
      },
}
};
</script>

<style>
.arrow-up:before {
  content: '\2191';
}

.arrow-down:before {
  content: '\2193';
}

.unchanged:before {
  content: '-';
}
</style>