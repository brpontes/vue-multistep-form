<script setup>
import Button from "../base/Button.vue";

defineProps({
  step: {
    type: Number,
    default: 1,
  },
});

const emits = defineEmits(["next-step", "prev-step"]);
</script>

<template>
  <footer>
    <Button
      v-if="step !== 1"
      label="Go Back"
      type="plain"
      @click="emits('prev-step')"
    />
    <span v-else></span>

    <Button v-if="step !== 4" label="Next Step" @click="emits('next-step')" />
    <Button v-else label="Confirm" type="secondary" />
  </footer>
</template>

<style lang="scss" scoped>
footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
</style>
