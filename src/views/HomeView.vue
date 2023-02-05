
<template>
  <main>
    <div
    style="height: 100%;"
    >
    <!-- <Transition name="fade" mode="in-out"> -->
      <!-- <el-icon v-if="viewIcon" :size="270" style="margin-top: 5rem;" class="red" id="rect1"><HomeFilled /></el-icon> -->
      <img :src="home" class="home" style="background-color: red;"/>
    <!-- </Transition>  -->
    <Transition name="fade" mode="in-out">
    <p v-if="viewTitle" style="font-size: 9rem;">Product-Page</p>
  </Transition> 
  </div>
  </main>
</template>
<script>
 import {
    HomeFilled,
  } from '@element-plus/icons-vue'
  import { ref, onMounted } from 'vue'
  import home from '../assets/home.svg'

  export default {
  components: {
    HomeFilled,
  },
  data() {
    return {
      viewIcon: false,
      viewTitle: false,
      home
    }
  },
  mounted() {
    setTimeout(() => {
      this.viewIcon = true
    }, 500);
    setTimeout(() => {
      this.viewTitle = true
    }, 1000);
  }
}

</script>

<style>
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
</style>
