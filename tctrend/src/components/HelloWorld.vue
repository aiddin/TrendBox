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
    compareValue: 10,
      trends: [
        { id: 1, direction: 'up' },
        { id: 2, direction: 'down' },
        { id: 3, direction: 'up' },
        { id: 4, direction: 'down' },
        { id: 4, direction: 'unchanged' },

      ],
    };
  },
  methods: {
    // Method to check if a value is the same, more or less than the compareValue
    checkValue(value) {
      if (value == this.compareValue) {
        return 'same';
      } else if (value > this.compareValue) {
        return 'more';
      } else {
        return 'less';
      }
    },
}
}
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