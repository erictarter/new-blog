<script setup lang="ts">
</script>

<template>
  <div id="/" class="footer d-flex justify-content-between align-items-center mt-4 py-3 px-3 px-sm-5">
    <div>
      <p class="fs-5 text-center">© Eric Tarter</p>
    </div>
    <div class="socials">
      <a target="_blank" href="https://github.com/erictarter">
        <i class="lni lni-github fs-3 mx-3"></i>
      </a>
      <a target="_blank" href="https://www.linkedin.com/in/eric-tarter-b2549a203/">
        <i class="lni lni-linkedin-original fs-3 mx-3"></i>
      </a>
    </div>
  </div>
</template>

<style scoped lang="scss">
.footer {
    border-top: 1px rgb(154, 156, 177) solid;

    a {
        color: rgb(54, 55, 65);
        margin-left: -1rem;
    }

    i {
    cursor: pointer;    

    }
    i:hover {
    color: hsl(188deg, 55%, 68%);
    transition: .2s ease all;        
    }

    p {
        margin: 0 !important;
    }
}
</style>