<script setup>
import { defineEmits } from "vue";

const emitCurrentStep = defineEmits(["update:current-step"]);

const handleEmitCurrentStep = (step) => {
  emitCurrentStep("update:current-step", step);
};

defineProps({
  data: {
    type: Object,
    default: () => ({}),
  },
});
</script>

<template>
  <li class="wizard-step-item" @click="handleEmitCurrentStep(data)">
    <span
      :class="[
        'wizard-step-item__step',
        data.active ? 'wizard-step-item__step--is-active' : null,
      ]"
    >
      {{ data.step }}
    </span>
    <div class="wizard-step-item__description">
      <span class="wizard-step-item__description--step">
        Step {{ data.step }}
      </span>
      <span class="wizard-step-item__description--current">
        {{ data.description }}
      </span>
    </div>
  </li>
</template>

<style lang="scss" scoped>
.wizard-step-item {
  display: flex;
  gap: 1rem;
  margin-left: 2rem;
  margin-bottom: 30px;
  cursor: pointer;

  &__step {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    color: var(--white);
    padding: 5px 15px;
    border: 1px solid var(--white);
    border-radius: 100%;
    transition: .2s all ease-out;

    &--is-active {
      color: var(--marine-blue);
      background-color: var(--light-blue);
      border: 1px solid transparent;
    }
  }

  &__description {
    text-transform: uppercase;
    display: flex;
    flex-direction: column;

    &--step {
      color: var(--light-gray);
      font-weight: 400;
      font-size: 13px;
    }

    &--current {
      color: var(--white);
      font-weight: 700;
      font-size: 14px;
    }
  }
}
</style>
