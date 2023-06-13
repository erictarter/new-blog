<script setup lang="ts">
  import Socials from './utilities/Socials.vue'
</script>

<template>
  <div
    id="/"
    class="footer d-flex justify-content-between align-items-center mt-4 blog-container">
    <div>
      <p class="fs-5 text-center">© Eric Tarter</p>
    </div>
    <Socials />
  </div>
</template>

<style scoped lang="scss">
  .footer {
    border-top: 1px rgb(154, 156, 177) solid;

    p {
      margin: 0 !important;
    }
  }
</style>
