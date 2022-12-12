<template>
  <div>
    <span v-for="trend in trends" :key="trend.id">
      <span v-if="trend.direction === 'up'" class="arrow-up"></span>
      <span v-if="trend.direction === 'down'" class="arrow-down"></span>
      <span v-if="trend.direction === 'unchanged' " class="unchanged"></span>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      trends: [
        { id: 1, direction: 'up' },
        { id: 2, direction: 'down' },
        { id: 3, direction: 'up' },
        { id: 4, direction: 'down' },
        { id: 4, direction: 'unchanged' },

      ],
    };
  },
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