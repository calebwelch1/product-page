
<template>
  <main>
    <!-- <div
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
  </div> -->
  <div class="product-container"
  >
    <div
    class="product-card"
    v-for="item in items.products"
    :key="item.id"
    >
      <!-- <VueSlickCarousel
      v-if="item.images.length > 0"
      :dots="true"
      v-for="image in item.images"
      :key="image.id">
      <img
      :src="image"
      alt="Product 1"
      style="max-height: 14rem; max-width: 18rem;"
      >
    </VueSlickCarousel> -->
    <Carousel :wrap-around="false">
    <Slide v-for="image in item.images" :key="image">
      <img
      :src="image"
      alt="Product 1"
      style="max-height: 14rem; max-width: 18rem;"
      >
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
      <h3>{{ item.title }}</h3>
      <p>{{item.description}}</p>
    </div>
  </div>
  </main>
</template>
<script>
import { onMounted } from 'vue';
import axios from 'axios'
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

// { "id": 1, "title": "iPhone 9", "description": "An apple mobile which is nothing like apple", 
// "price": 549, "discountPercentage": 12.96, "rating": 4.69, "stock": 94, "brand": "Apple",
// "category": "smartphones", "thumbnail": "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
// "images": [ "https://i.dummyjson.com/data/products/1/1.jpg", "https://i.dummyjson.com/data/products/1/2.jpg", "https://i.dummyjson.com/data/products/1/3.jpg", "https://i.dummyjson.com/data/products/1/4.jpg", "https://i.dummyjson.com/data/products/1/thumbnail.jpg" ] }'
// const MyCard = app.component(Card);

export default {
  components: {
    // shorthand
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      items: [],
    };
  },
  async created() {
    try {
      const res = await axios.get(`https://dummyjson.com/products`);
      this.items = res.data;
      console.log(this.items);
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

* {
      box-sizing: border-box;
}
    
    body {
      font-family: Arial, sans-serif;
      margin: 0;
    }
    
    p {
      color: black;
    }
    
    .product-container {
      display: flex;
  flex-wrap: wrap;
    }
    
    .product-card {
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 20px;
      margin: 4px;
      background-color: #fff;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      width: 30vw;
    }

    @media (max-width: 1490px) {
      .product-container {
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      }
      .product-card {
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 2px;
      margin-bottom: 25px;
      margin: 4px;
      background-color: #fff;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      width: 70vw;
    }
    }
    
    .product-card img {
      width: 100%;
      height: auto;
      margin-bottom: 10px;
    }
    
    .product-card h3 {
      font-size: 18px;
      margin: 0;
      margin-bottom: 10px;
    }
    
    .product-card p {
      font-size: 14px;
      margin: 0;
    }
</style>
