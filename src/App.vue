<template>
  <BlogSelect @blog-switch="blogToggle" :title="blogTitle" />
  <div class="d-sm-flex flex-column align-items-center">
    <BlogHeader :title="blogTitle" :date="blogDate" :readTime="readTime" />
    <BlogOne v-if="blogSelect === '1'" />
    <BlogTwo v-if="blogSelect === '2'" />
    <BlogFooter />
  </div>
</template>

<script setup lang="ts">
  import BlogSelect from './components/BlogSelect.vue'
  import BlogOne from './components/BlogOne.vue'
  import BlogTwo from './components/BlogTwo.vue'
  import BlogFooter from './components/BlogFooter.vue'
  import BlogHeader from './components/BlogHeader.vue'
  import { ref } from 'vue'

  const blogSelect = ref('1')
  const blogTitle = ref('Piano App w/Tone JS')
  const blogDate = ref('November 21, 2020')
  const readTime = ref('Read Time 5 minutes')

  function blogToggle(value: any) {
    blogSelect.value = value
    if (value === '1') {
      blogTitle.value = 'Piano App w/Tone JS'
      blogDate.value = 'November 21, 2020'
      readTime.value = 'Read Time 5 minutes'
    } else {
      blogTitle.value = 'Simple Tips & Tools'
      blogDate.value = 'November 27, 2020'
      readTime.value = 'Read Time 2 minutes'
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    overflow-x: hidden;
  }
</style>
