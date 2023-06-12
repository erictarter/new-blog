<script setup lang="ts">
import BlogSelect from './components/BlogSelect.vue';
import BlogOne from './components/BlogOne.vue'
import BlogFooter from './components/BlogFooter.vue'
</script>

<template>
  <BlogSelect />
  <BlogOne />
  <BlogFooter />
</template>

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
