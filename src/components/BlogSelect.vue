<script setup lang="ts">
  defineProps<{ title: string }>()

  import { ref, defineEmits } from 'vue'

  const toggleBlog = ref('1')
  const emits = defineEmits(['blog-switch'])

  function blogSwitchOne() {
    toggleBlog.value = '1'
    emits('blog-switch', '1')
  }
  function blogSwitchTwo() {
    toggleBlog.value = '2'
    emits('blog-switch', '2')
  }
</script>
<template>
  <div class="blog-header fs-2">
    <div class="image-overlay"></div>
    <div
      :class="toggleBlog === '1' ? 'header-image' : 'header-image d-none'"
      style="
        background-image: url('https://images.unsplash.com/photo-1487017159836-4e23ece2e4cf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1171&q=80');
      "></div>
    <div
      :class="toggleBlog === '2' ? 'header-image' : 'header-image d-none'"
      style="
        background-image: url('https://images.unsplash.com/photo-1533136036465-1861830963f6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80');
      "></div>
    <div
      class="title d-flex align-items-center justify-content-center w-100 h-100">
      <h1 class="fs-1 px-3 text-center">
        {{ title }}
      </h1>
    </div>
    <div class="select-indicators d-flex justify-content-center w-100">
      <div
        @click="blogSwitchOne"
        :class="
          toggleBlog === '1'
            ? 'indicator selected-indicator mx-1'
            : 'indicator mx-1'
        "></div>
      <div
        @click="blogSwitchTwo"
        :class="
          toggleBlog === '2'
            ? 'indicator selected-indicator mx-1'
            : 'indicator mx-1'
        "></div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .blog-header {
    height: 100vh;
    width: 100vw;
  }
  .header-image {
    position: absolute;
    background: url('') no-repeat center/cover;
    min-width: 100%;
    height: 100vh;
    overflow-x: hidden !important;
  }
  .select-indicators {
    position: absolute;
    left: 0;
    top: 85vh;
    z-index: 100;
  }
  .indicator {
    width: 75px;
    height: 20px;
    border: 2px solid rgba(255, 255, 255, 0.75);
    border-radius: 6px;
    cursor: pointer;
    transition: 0.2s ease all;
  }

  .indicator:hover {
    background-color: rgba(255, 255, 255, 0.45);
    transition: 0.2s ease all;
  }

  .selected-indicator {
    background-color: rgba(207, 232, 226, 0.8);
  }

  .image-overlay {
    position: absolute;
    z-index: 99;
    width: 100%;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.7);
  }

  .title {
    z-index: 100;
    position: absolute;
    left: 0;
    top: 0;
    color: white;
  }
</style>
