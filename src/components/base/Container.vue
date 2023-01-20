<script setup></script>

<template>
  <main class="container">
    <slot />
  </main>
</template>

<style lang="scss">
.container {
  margin: 5% auto;
  max-width: 90%;
  width: 1200px;
  background-color: var(--white);
  padding: 10px;
  border-radius: 10px;
  display: flex;
  gap: 1rem;
}
</style>
