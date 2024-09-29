<script setup></script>

<template>
  <main class="app-wrapper">
    <section class="container">
      <slot />
    </section>
  </main>
</template>

<style lang="scss">
.app-wrapper {
  display: flex;
  width: 100%;
  height: 100vh;
  justify-content: center;
  align-items: center;
  background-color: var(--magnolia);

  .container {
    display: flex;
    align-items: center;
    background-color: var(--white);
    border-radius: 10px;
    width: 100%;
    max-width: 1440px;
    padding: 12px;
    margin: 2rem;
    overflow-x: auto;
  }
}
</style>
