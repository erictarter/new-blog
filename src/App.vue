<script setup lang="ts">
import BlogHeader from './components/BlogHeader.vue';
import BlogMain from './components/BlogMain.vue'
import BlogFooter from './components/BlogFooter.vue'
</script>

<template>
  <BlogHeader />
  <BlogMain />
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
