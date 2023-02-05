<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
  import {
    Document,
    Menu as IconMenu,
    Location,
    Setting,
    HomeFilled,
    Shop,
    Avatar
  } from '@element-plus/icons-vue'

  const isCollapse = ref(true)
  const handleOpen = (key, keyPath) => {
    console.log(key, keyPath)
  }
  const handleClose = (key, keyPath) => {
    console.log(key, keyPath)
  }
</script>

<template>
  <div>
  <!-- <el-radio-group v-model="isCollapse">
      <el-radio-button :label="false">expand</el-radio-button>
      <el-radio-button :label="true">collapse</el-radio-button>
    </el-radio-group> -->
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      :collapse="isCollapse"
      @open="handleOpen"
      @close="handleClose"
    >
      <!-- this.$router.push('UIPortfolio') -->
    <el-switch v-model="isCollapse" />
      <el-menu-item index="1" @click="$router.push('/')">
        <el-icon :size="30"><HomeFilled /></el-icon>
        <template #title>Home</template>
      </el-menu-item>
      <el-menu-item index="2"  @click="$router.push('Dashboard')">
        <el-icon :size="30"><icon-menu /></el-icon>
        <template #title>Dashboard</template>
      </el-menu-item>
      <el-menu-item index="3"  @click="$router.push('Shop')">
        <el-icon :size="30"><Shop /></el-icon>
        <template #title>Shop</template>
      </el-menu-item>
      <el-menu-item index="4">
        <el-icon :size="30"><setting /></el-icon>
        <template #title>Settings</template>
      </el-menu-item>
      <el-menu-item style="pointer-events: none;">
      </el-menu-item>
      <el-menu-item style="pointer-events: none;">
      </el-menu-item>
      <el-menu-item style="pointer-events: none;">
      </el-menu-item>
      <el-menu-item style="pointer-events: none;">
      </el-menu-item>
      <el-menu-item style="pointer-events: none;">
      </el-menu-item>
       <el-menu-item style="pointer-events: none;">
      </el-menu-item>
      <el-menu-item index="1" @click="$router.push('Profile')">
        <el-icon :size="30"><Avatar /></el-icon>
        <template #title>Profile</template>
      </el-menu-item>
    </el-menu>
    </div>
  <Transition name="fade" mode="in-out">
  <RouterView :class="`${isCollapse ? 'router-width-collapsed' : 'router-width'}`"/>
  </Transition>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

* {
  font-family: 'Roboto', sans-serif !important;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

main {
  overflow-y: scroll;
}

.router-width {
  width: 86vw;
  max-width: 86vw;
}

.router-width-collapsed {
  width: 95vw;
  max-width: 95vw;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 14vw;
    min-height: 400px;
    min-width: 12rem;
    height: 99vh;
  }

.el-menu--collapse {
  width: 5vw;
  min-width: 4rem;
    min-height: 400px;
    height: 99vh;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
