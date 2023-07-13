
<template>
  <main>
    <div
    style="height: 100%;"
    class="force-colors"
    >
    <div class="container">
      <video class="bg-video" autoplay loop>
        <source src="https://imgur.com/2cSaKIt.mp4" type="video/mp4" />
      </video>
      <p class="text">HOME</p>
    </div>
    <p
    style="color:white; font-weight: 500; font-size: 1.25rem;margin-left: 20%; margin-right: 20%;"
    >
    HOME is a collection of projects by Caleb Welch intended to explore and showcase
      modern front end design. <br> This site is under construction so please check back often. <br> 

      If you'd like to see my other work connect with me -
    </p>
    <div class="product-container"
  >
    <div
    class="product-card"
    >
    <p>MoMA</p>
    </div>
    <div
    class="product-card"
    >
    <p>SHOP</p>
    </div>
  </div>
</div>
  </main>
</template>
<script>
  import { ref, onMounted } from 'vue'
  import home from '../assets/home.svg'
  import axios from 'axios'


  export default {
  components: {
  },
  data() {
    return {
      viewIcon: false,
      viewTitle: false,
      home,
      windowWidth: window.innerWidth,
      columns: 3,
      imageNum: 10,
      images:[],
      text:'',
    }
  },
  async created() {
    try {
      const res = await axios.get(`https://collectionapi.metmuseum.org/public/collection/v1/objects/${99}`);
      this.images = res.data;
      console.log(res);
    } catch (error) {
      console.log(error);
    }
  },
  mounted() {
    setTimeout(() => {
      this.viewIcon = true
    }, 500);
    setTimeout(() => {
      this.viewTitle = true
    }, 1000);
    this.$nextTick(() => {
      window.addEventListener('resize', this.onResize);
    })
  },
  beforeDestroy() { 
    window.removeEventListener('resize', this.onResize); 
  },
  methods: {  
    onResize() {
      this.windowWidth = window.innerWidth
    },
    async search(val) {
      const res = await axios.get(`https://collectionapi.metmuseum.org/public/collection/v1/search?q=${val}`)
      console.log(res);
    },
  }
}

</script>

<style>
.row {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.column {
  display: flex; /* Set column to flex layout */
  flex-direction: column; /* Set column to column direction */
  flex: 1; /* Allow column to grow to fill available space */
}

/* Container should be full height and full width */
.container {
  position: relative;
  width: 100%;
  height: 50vh;
}

.container > .bg-video {
  width: 100%;
  height: 100%;
}

.force-colors {
  background-color: #000 !important;
  color: #fff !important;
}

/* background-color and color should be the same as the below otherwise it won't work */
.container > .text {
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
  background-color: #000;
  color: #fff;
  font-weight: 900;
  font-size: 300px;
  font-family: sans-serif;
  /* Mix Blend Mode does the all magic */
  mix-blend-mode: multiply;
  user-select: none;
}

@media (max-width: 800px){ 
}
.mulish {
  font-family: 'Mulish', sans-serif !important;
}

.product-container {
      display: flex;
  flex-wrap: wrap;
  margin-left: 30%;
  margin-right: 30%;

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
</style>
