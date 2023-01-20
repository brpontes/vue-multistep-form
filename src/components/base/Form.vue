<script setup>
defineProps({
  currentStep: {
    type: Object,
    default: () => ({}),
  },
});
</script>

<template>
  <form class="wrapper-form">
    <component :is="currentStep" />
  </form>
</template>

<style lang="scss" scoped>
.wrapper-form {
}
</style>
