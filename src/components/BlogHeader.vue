<script setup lang="ts">
  import Socials from './utilities/Socials.vue'
  import Divider from './utilities/Divider.vue'

  defineProps<{ title: string; date: string; readTime: string }>()
</script>
<template>
  <div class="blog-header blog-container w-100">
    <div class="profile d-flex justify-content-between align-items-center">
      <div class="profile-avatar"></div>
      <div class="profile-links">
        <Socials />
        <button class="site-btn">
          <!-- CREATE BRAND LOGO HERE -->
          ET
          <a href="www.erictarter.com"></a>
        </button>
      </div>
    </div>
    <div class="blog-info d-flex flex-column align-items-start mt-5">
      <h1 class="blog-title">{{ title }}</h1>
      <p class="date-written mb-1 mt-2">{{ date }}</p>
      <p class="read-time">{{ readTime }}</p>
    </div>
    <Divider />
  </div>
</template>

<style scoped lang="scss">
  .profile-avatar {
    width: 75px;
    height: 75px;
    border-radius: 50%;
    background: url(../assets/personal-picture.jpg) no-repeat center/cover;
  }

  .site-btn {
    border-radius: 6px;
    color: #42403f;
    background-color: mintcream;
    width: 100%;
    border: 2px solid #42403f;
    transition: 0.2s ease all;
  }

  .site-btn:hover {
    box-shadow: 0px 6px 12px 0px rgba(0, 0, 0, 0.4);
    transition: 0.2s ease all;
  }

  .blog-title {
    font-size: 36px;
  }

  .read-time {
    color: #7e9292;
    font-size: 14px;
  }
</style>
