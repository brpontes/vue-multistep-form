<script setup>
defineProps({
  title: {
    type: String,
    default: "",
  },
  subtitle: {
    type: String,
    default: "",
  },
});
</script>

<template>
  <section class="header">
    <header>
      <h1 class="header__title">{{ title }}</h1>
      <h2 class="header__subtitle">{{ subtitle }}</h2>
    </header>
  </section>
</template>

<style lang="scss">
.header {
  margin: 40px 4rem 10px;

  &__title {
    font-size: 32px;
    font-weight: 700;
    color: var(--marine-blue);
    margin: 0;
  }

  &__subtitle {
    font-size: 16px;
    font-weight: 400;
    color: var(--cool-gray);
  }
}
</style>
