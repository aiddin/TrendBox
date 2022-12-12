<template>
  <div >
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  // Initialize two objects in the data object of your Vue component
data() {
  return {

    
    object1: {
      id: 1,
      name: 'John'
    },
    object2: {
      id: 2,
      name: 'Jane'
    }
  }
},

// Use some() to check if there is an element with the same id in object1 and object2
method: {
  hasSameId() {
    const huh = this.object1.some(item1 => item1.id === this.object2.id);
    return huh;
  },
  updatedArray() {
    return [this.object1, this.object2].filter(item => {
      // Use some() to check if there is an element with the same id in the array
      const exists = this.array.some(
        i => i !== item && i.id === item.id
      );
      // If an element with the same id is not found, keep the element in the array
      return console.log(exists);
    });
  }
},
mounted() {
  console.log(this.hasSameId());
  console.log(this.updatedArray());
}

// Use filter() to create a new array that only contains elements with unique id values

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
