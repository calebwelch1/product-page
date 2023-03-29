
<template>
  <main>
    <div
    style="height: 100%;"
    >
    <!-- <Transition name="about"></Transition> -->
    <Transition name="fade" mode="in-out">
    <p v-if="viewTitle" style="font-size: 9rem;" class="mulish">MoMA</p>
  </Transition> 
    <div class="container">
    {{ windowWidth }}
      <div
      v-if="this.windowWidth > 780"
      class="row"
      >
        <div
        v-for="col in 3"
        :class="`column${col}`"
        >
           <img
           />
        </div>
      </div>
      <div
      class="column"
      v-else
      >
        
      </div>
    </div>
  </div>
  </main>
</template>
<script>
 import {
    HomeFilled,
  } from '@element-plus/icons-vue'
  import { ref, onMounted } from 'vue'
  import home from '../assets/home.svg'
  import axios from 'axios'


  export default {
  components: {
    HomeFilled,
  },
  data() {
    return {
      viewIcon: false,
      viewTitle: false,
      home,
      windowWidth: window.innerWidth,
      columns: 3,
      images:[],
    }
  },
  async created() {
    try {
      const res = await axios.get(`https://collectionapi.metmuseum.org/public/collection/v1/objects`);
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
    }
  }
}

</script>

<style>
.row {
  display: flex;
  flex-direction: row;
  width: 100%;
}
.container {
  display: flex; /* Set container to flex layout */
  flex-direction: column; /* Set container to column direction */
}

.column {
  display: flex; /* Set column to flex layout */
  flex-direction: column; /* Set column to column direction */
  flex: 1; /* Allow column to grow to fill available space */
}

@media (max-width: 800px){ 
}
.mulish {
  font-family: 'Mulish', sans-serif !important;
}

.home {
  fill: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(9,51,121,1) 0%, rgba(226,0,255,1) 100%) !important;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
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

.about-enter-active {
  transition: all 0.5s ease-out;
}

.about-leave-active {
  transition: all 0.5s ease-out;
}

.about-enter-from,
.about-leave-to {
  transform: translateX(-200px);
  opacity: 0;
}
</style>
