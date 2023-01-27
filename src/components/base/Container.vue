<script setup></script>

<template>
  <main class="container">
    <slot />
  </main>
</template>

<style lang="scss">
.container {
  @apply flex gap-4 mt-5 mx-auto p-2.5 w-[1200px] max-w-7xl rounded-[10px] bg-white;
}
</style>
