<script setup>
import { RouterLink, RouterView } from 'vue-router'
import BurgerMenu from './components/BurgerMenu.vue'
import { ref } from 'vue'

const menuActive = ref(false)
</script>

<template>
  <BurgerMenu @toggle-menu="menuActive = !menuActive" :active="menuActive" />
  <header></header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}
</style>
