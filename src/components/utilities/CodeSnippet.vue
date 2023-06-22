<script setup lang="ts">
  import { ref } from 'vue'

  defineProps<{ code: string; lang: string }>()

  const codeElement = ref<HTMLElement | null>(null)

  const copyCode = () => {
    const code = codeElement.value?.textContent
    if (code) {
      navigator.clipboard
        .writeText(code)
        .then(() => {
          alert('Code copied to clipboard!')
        })
        .catch((error) => {
          console.error('Failed to copy code:', error)
        })
    }
  }
</script>
<template>
  <div class="top-snippet d-flex align-items-center justify-content-between">
    <span class="mx-3">{{ lang }}</span>
    <button class="copy-button mx-3" @click="copyCode">
      <span><i class="lni lni-clipboard"></i></span> Copy Code
    </button>
  </div>
  <pre class="code-snippet">
      <code ref="codeElement" class="d-flex text-start fs-5 px-4 px-sm-5">
        {{ code }}
      </code>
    </pre>
</template>

<style scoped lang="scss">
  .top-snippet {
    height: 50px;
    background-color: #e4b4ef !important;
    color: #282828;
    width: 100%;
  }
  .code-snippet {
    background-color: #f1f1f1;
  }

  .copy-button {
    cursor: pointer;
    border: none;
    background-color: #e4b4ef;
    color: #282828;
  }

  pre {
    white-space: pre-line;
  }
</style>
