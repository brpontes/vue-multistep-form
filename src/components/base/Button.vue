<script setup>
defineProps({
  label: {
    type: String,
    default: "",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  type: {
    type: String,
    default: "primary",
  },
});

const emits = defineEmits(["click"]);

const onClick = (event) => {
  event.preventDefault();
  emits("click");
};
</script>

<template>
  <button
    :class="['wrapper-button', `wrapper-button-${type}`]"
    :disabled="disabled"
    @click="onClick"
  >
    {{ label }}
  </button>
</template>

<style lang="scss" scoped>
.wrapper-button {
  color: var(--white);
  padding: 12px 20px;
  border-radius: 0.5rem;
  cursor: pointer;

  &-primary {
    background-color: var(--marine-blue);
  }

  &-secondary {
    background-color: var(--purplish-blue);
    color: var(--white);
  }

  &-plain {
    background-color: var(--white);
    color: var(--cool-gray);
    padding: 12px 0;
  }

  &:disabled {
    background-color: var(--cool-gray);
    cursor: not-allowed;
  }
}
</style>
