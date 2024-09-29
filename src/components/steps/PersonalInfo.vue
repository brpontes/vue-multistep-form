<script setup>
import Header from "../base/Header.vue";
import Input from "../base/Input.vue";

const props = defineProps({
  form: {
    type: Object,
    default: () => ({}),
  },
});
const emit = defineEmits(["update:form"]);

const onInput = (field, value) => emit("update:form", { [field]: value });
</script>

<template>
  <section class="wrapper-personal-info">
    <Header
      title="Personal info"
      subtitle="Please provide your name, email address, and phone number."
    />
    <section class="wrapper-personal-info__content">
      <label class="secao">
        Name
        <Input
          :value="form.name"
          name="name"
          placeholder="e.g. Stephen King"
          @input="onInput('name', $event)"
        />
      </label>
      <label class="secao">
        Email Address
        <Input
          :value="form.email"
          name="email"
          placeholder="e.g. stephenking@lorem.com"
          @input="onInput('email', $event)"
        />
      </label>
      <label class="secao">
        <span>Phone Number</span>
        <Input
          :value="form.phone"
          name="phone"
          placeholder="e.g. +1 234 567 890"
          @input="onInput('phone', $event)"
        />
      </label>
    </section>
  </section>
</template>

<style lang="scss" scoped>
.wrapper-personal-info {
  &__content {
    display: flex;
    flex-direction: column;

    .secao {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      color: var(--marine-blue);

      &:not(:last-child) {
        margin-bottom: 1.5rem;
      }
    }
  }
}
</style>
