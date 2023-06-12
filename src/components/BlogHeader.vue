<script setup lang="ts">
</script>
<template>
  <div class="blog-header">
    <div class="profile d-flex justify-content-between align-items-center">
        <div class="profile-avatar"></div>
        <div class="profile-links">
            <div class="socials">
              <a target="_blank" href="https://github.com/erictarter">
                <i class="lni lni-github fs-3 me-2"></i>
              </a>
              <a target="_blank" href="https://www.linkedin.com/in/eric-tarter-b2549a203/">
                <i class="lni lni-linkedin-original fs-3"></i>
              </a>
            </div>
            <button>
                <a href="www.erictarter.com"></a>
            </button>
        </div>
    </div>
    <h1 class="blog-title"></h1>
    <p class="date-written"></p>
    <p class="read-time"></p>
  </div>
</template>


<style scoped lang="scss">
    .profile-avatar {
        width: 125px;
        height: 125px;
        border-radius: 50%;
        border: 2px solid #42403f;
    }
    i {
        color: #42403f;
    }
    i:hover {
        box-shadow: rgba(255, 255, 255, 0.1) 0px 1px 1px 0px inset, rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
    }
</style>
