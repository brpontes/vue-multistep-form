<script setup>
import WizardStep from "./WizardStep.vue";
import BgWizardDesktop from "@/assets/bg-wizard-desktop.svg";

defineProps({
  steps: {
    type: Array,
    default: [],
  },
});

const emitCurrentStep = defineEmits(["update:current-step"]);

const handleEmitCurrentStep = (step) => {
  emitCurrentStep("update:current-step", step);
};
</script>

<template>
  <article
    class="wizard"
    :style="{
      backgroundImage: `url(${BgWizardDesktop})`,
      backgroundRepeat: 'no-repeat',
      backgroundSize: 'cover',
    }"
  >
    <ul class="wizard-steps">
      <WizardStep
        v-for="step in steps"
        :key="step.step"
        :data="step"
        @update:current-step="handleEmitCurrentStep"
      />
    </ul>
  </article>
</template>

<style lang="scss" scoped>
.wizard {
  width: 280px;
  height: 578px;

  &-steps {
    margin-top: 40px;
    list-style-type: none;
  }
}
</style>
