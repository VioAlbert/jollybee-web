<script setup lang="ts">
  import HeaderBar from './components/HeaderBar.vue'
  import AboutPage from './components/pages/AboutPage.vue'
  import LearnPage from './components/pages/LearnPage.vue'
  import RegisterPage from './components/pages/RegisterPage.vue'
  import FooterBar from './components/FooterBar.vue'
  import { ref, computed } from 'vue'

  const pages = [
    {
      name: 'About',
      component: AboutPage,
    },
    {
      name: 'Learn',
      component: LearnPage,
    },
    {
      name: 'Register',
      component: RegisterPage,
    },
  ]

  const pageItems = computed(() => {
    return pages.map((e) => { return e.name })
  })
  const pageComponent = computed(() => {
    return pages.map((e) => { return e.component })
  })

  const activePageIndex = ref(0)

  const changePage = (x : number) => {
    activePageIndex.value = x
  }
</script>

<template>
  <div class="container max-w-xl mx-auto">
    <img src="/images/logo_hexagon.svg" alt="" class="mx-auto my-3 h-10 block">
    <HeaderBar :pages="pageItems" :activePageIndex="activePageIndex" @change-page="changePage" />
    <div class="border border-white p-10 h-[80vh] scrollable">
      <component :is="pageComponent[activePageIndex]" @change-page="changePage" />
    </div>
    <FooterBar />
  </div>
</template>

<style scoped>
.scrollable {
  overflow: auto;
  scrollbar-color: #7d7d7d;
}

.scrollable::-webkit-scrollbar{
  width: var(--pseudo-sb-w);
}

.scrollable::-webkit-scrollbar-track{
  background-color: #7d7d7d;
}

.scrollable::-webkit-scrollbar-thumb{
  background: white;
}
</style>
