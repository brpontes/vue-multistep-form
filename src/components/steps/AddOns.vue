<script setup>
import Header from "../base/Header.vue";

const props = defineProps({
  form: {
    type: Object,
    default: () => ({}),
  },
});
</script>

<template>
  <Header
    title="Pick add-ons"
    subtitle="Add-ons help enhance your gaming experience."
  />
</template>
