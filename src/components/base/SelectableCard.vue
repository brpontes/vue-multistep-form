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
    <img
      :src="`./src/assets/icon-${plan.plan}.svg`"
      :alt="`icon-${plan.plan}`"
      :title="`icon-${plan.plan}`"
      width="50"
    />

    <div class="selectable-card__details">
      <span class="selectable-card__details--plan">{{ plan.plan }}</span>
      <span class="selectable-card__details--value">{{ planValue }}</span>
      <span v-if="periodicity === 'yearly'">2 months free</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.selectable-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 3rem;
  padding: 1rem;
  background-color: var(--white);
  border: 1px solid var(--marine-blue);
  border-radius: 10px;

  &__details {
    display: flex;
    flex-direction: column;
    gap: 6px;

    &--plan {
      color: var(--marine-blue);
      font-weight: 500;
      text-transform: capitalize;
    }

    &--value {
      color: var(--cool-gray);
      font-size: 14px;
    }
  }
}
</style>
