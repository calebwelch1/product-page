
<template>
  <main>
    <div
    v-for="item in items.products"
    :key="item.id"
    style="border: 1px solid white;"
    >
    <div class="flex-row">
      <div style="border 1px solid white; padding: 1rem;">
        <img
        :src="item.images[0]"
        style="max-height: 14rem; max-width: 18rem;"
        />
    </div>
      <div>
        <p>{{ item.title }}</p>
        <p>{{ item.brand }}</p>
        <p>{{ item.smartphones }}</p>
        <p>{{ item.description }}</p>
        <p>${{ item.price }}</p>
      </div>
  </div>
  </div>
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
