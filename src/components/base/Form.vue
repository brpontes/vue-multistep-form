<script setup>
import { reactive } from "vue";
import Footer from "./Footer.vue";

defineProps({
  currentStep: {
    type: Object,
    default: () => ({}),
  },
});

const form = reactive({
  name: "",
  email: "",
  phone: "",
});

const emits = defineEmits(["next-step", "prev-step"]);

const updateForm = (data) => {
  Object.assign(form, data);
};
</script>

<template>
  <form class="wrapper-form">
    <div class="wrapper-form__content">
      <component
        :is="currentStep.component"
        :form="form"
        @update:form="updateForm"
      />
      <Footer
        :step="currentStep.step"
        @next-step="emits('next-step')"
        @prev-step="emits('prev-step')"
      />
    </div>
  </form>
</template>

<style lang="scss" scoped>
.wrapper-form {
  display: flex;
  justify-content: center;
  width: 100%;
  min-width: 450px;

  &__content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 70%;
    margin-right: 1rem;
    gap: 2rem 0;

    > section {
      display: flex;
      flex-direction: column;
      gap: 2rem;
      width: 100%;
    }
  }
}
</style>
