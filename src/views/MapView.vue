
<template>
  <main>
    da map
  </main>
</template>
<script>
import { onMounted } from 'vue';
import axios from 'axios'
// { "id": 1, "title": "iPhone 9", "description": "An apple mobile which is nothing like apple", 
// "price": 549, "discountPercentage": 12.96, "rating": 4.69, "stock": 94, "brand": "Apple",
// "category": "smartphones", "thumbnail": "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
// "images": [ "https://i.dummyjson.com/data/products/1/1.jpg", "https://i.dummyjson.com/data/products/1/2.jpg", "https://i.dummyjson.com/data/products/1/3.jpg", "https://i.dummyjson.com/data/products/1/4.jpg", "https://i.dummyjson.com/data/products/1/thumbnail.jpg" ] }'
// const MyCard = app.component(Card);

export default {
  // components: {
  //   // shorthand
  //   Card,
  // },
  data() {
    return {
      items: [],
    };
  },
  async created() {
    try {
      const res = await axios.get(`https://dummyjson.com/products`);
      this.items = res.data;
    } catch (error) {
      console.log(error);
    }
  },
}
onMounted(() => {
  el.value // <div>
})

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@600&display=swap');

* {
  font-family: 'Comfortaa', 'Avenir', 'Arial', 'sans-serif' !important
}

body{
  margin:0 !important;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: slate-grey;
  background-color: transparent;
}
.hi{
  color:black;
}

.flex-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

@media (max-width: 900px) {
  .flex-row {
    display: flex;
  flex-direction: column;
  justify-content: space-between;
  }
}
</style>
