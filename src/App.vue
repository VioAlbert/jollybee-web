<script setup lang="ts">
  import HeaderBar from './components/HeaderBar.vue'
  import AboutPage from './components/pages/AboutPage.vue'
  import LearnPage from './components/pages/LearnPage.vue'
  import RegisterPage from './components/pages/RegisterPage.vue'
  import { ref, computed } from 'vue'

  const pages = [
    {
      name: 'About',
      component: AboutPage
    },
    {
      name: 'Learn',
      component: LearnPage
    },
    {
      name: 'Register',
      component: RegisterPage
    },
  ]

  const pageItems = computed(() => {
    return pages.map((e) => { return e.name })
  })
  const pageComponent = computed(() => {
    return pages.map((e) => { return e.component })
  })

  const activePageIndex = ref(0)
</script>

<template>
  <div class="container max-w-xl mx-auto">
    <img src="./assets/logo_hexagon.svg" alt="" class="mx-auto my-3 h-10 block">
    <HeaderBar :pages="pageItems" @change-page="(x) => activePageIndex = x" />
    <div class="border border-white">
      <component :is="pageComponent[activePageIndex]" />
    </div>
  </div>
</template>

<style scoped>
</style>
