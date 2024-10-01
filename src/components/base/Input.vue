<script setup>
defineProps({
  name: {
    type: String,
    default: "",
  },
  placeholder: {
    type: String,
    default: "",
  },
  hasError: {
    type: Boolean,
    default: false,
  },
  modelValue: {
    type: String,
  },
});

defineEmits(["update:modelValue", "input"]);
</script>

<template>
  <input
    type="text"
    :placeholder="placeholder"
    :name="name"
    :class="['wrapper-input', hasError ? 'wrapper-input-has-error' : null]"
    @input="
      $emit('update:modelValue', $event.target.value);
      $emit('input', $event.target.value);
    "
  />
</template>

<style lang="scss" scoped>
.wrapper-input {
  border: 1px solid var(--light-gray);
  outline: none;
  padding: 0 1rem;
  border-radius: 0.5rem;
  height: 50px;
  font-weight: 500;
  font-family: "Ubuntu", sans-serif;
  color: var(--marine-blue);

  &:focus {
    border: 1px solid var(--purplish-blue);
  }

  &-has-error,
  &-has-error:focus {
    border: 1px solid var(--strawberry-red);
  }
}
</style>
