<script setup>
import { computed } from "vue";

const props = defineProps({
  plan: {
    type: Object,
    default: () => ({}),
  },
  periodicity: {
    type: String,
    default: null,
  },
});

const planValue = computed(() => {
  const periodicity = props.periodicity === "monthly" ? "mo" : "yr";
  const { value } = props.plan[props.periodicity];

  return `$${value}/${periodicity}`;
});
</script>

<template>
  <div class="selectable-card">
    <img :src="`./src/assets/icon-${plan.plan}.svg`" />

    <div class="plan-details">
      <span>{{ plan.plan }}</span>
      <span class="plan-details__value">{{ planValue }}</span>
      <span v-if="periodicity === 'yearly'">2 months free</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.selectable-card {
  padding: 10px;
  background-color: var(--white);
  border: 1px solid var(--marine-blue);
  border-radius: 10px;

  .plan-details {
    display: flex;
    flex-direction: column;

    :first-child {
      text-transform: capitalize;
    }

    &__value {
      color: var(--cool-gray);
      font-size: 14px;
    }
  }
}
</style>
