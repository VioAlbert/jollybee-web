<script setup lang="ts">
  defineProps<{
    pages: Array<String>
  }>()
</script>

<template>
  <div class="flex">
    <button v-for="(page, index) in pages"
      class="border border-white flex-grow text-center text-xl p-1"
      @click="$emit('changePage', index)">
      {{page}}
    </button>
  </div>
</template>

<style scoped>
</style>
