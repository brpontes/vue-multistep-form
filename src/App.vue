<script setup>
import { shallowRef, computed } from "vue";
import Container from "./components/base/Container.vue";
import Form from "./components/base/Form.vue";
import Wizard from "./components/wizard/Wizard.vue";

import PersonalInfo from "./components/steps/PersonalInfo.vue";
import SelectPlan from "./components/steps/SelectPlan.vue";
import AddOns from "./components/steps/AddOns.vue";
import Summary from "./components/steps/Summary.vue";

const steps = shallowRef([
  { step: 1, description: "Your info", active: true, component: PersonalInfo },
  { step: 2, description: "Select plan", active: false, component: SelectPlan },
  { step: 3, description: "Add-ons", active: false, component: AddOns },
  { step: 4, description: "Summary", active: false, component: Summary },
]);

const currentActiveStep = computed(() => {
  const [currentStep] = steps.value.filter((step) => step.active);
  return currentStep;
});

const updateStep = (action) => {
  const step =
    action === "next"
      ? currentActiveStep?.value?.step + 1
      : currentActiveStep?.value?.step - 1;

  setCurrentActiveStep({ step });
};

const setCurrentActiveStep = (currentStep) => {
  steps.value = steps.value.map((step) => ({
    ...step,
    active: currentStep.step === step.step,
  }));
};
</script>

<template>
  <Container>
    <Wizard :steps="steps" @update:current-step="setCurrentActiveStep" />
    <Form
      :current-step="currentActiveStep"
      @next-step="updateStep('next')"
      @prev-step="updateStep('prev')"
    />
  </Container>
</template>
