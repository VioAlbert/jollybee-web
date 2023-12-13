<script setup lang="ts">
  defineProps<{
    pages: Array<String>,
    activePageIndex: Number
  }>()
</script>

<template>
  <div class="flex">
    <button v-for="(page, index) in pages"
      class="border border-white flex-grow text-center text-xl p-1"
      :class="[
        activePageIndex === index ? ['bg-white', 'text-[#434343]'] : ''
      ]"
      @click="$emit('changePage', index)">
      {{page}}
    </button>
  </div>
</template>

<style scoped>
</style>
