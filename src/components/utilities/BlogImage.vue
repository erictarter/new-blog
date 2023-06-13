<script setup lang="ts">
  defineProps<{ url: string }>()
</script>
<template>
  <img :src="url" class="blog-image" />
</template>

<style scoped lang="scss">
  .blog-image {
    width: 100%;
  }
</style>
