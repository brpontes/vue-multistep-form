<script setup>
defineProps({
  periodicity: {
    type: String,
    default: null,
  },
});

const emits = defineEmits(["update:periodicity"]);

const updatePeriodicity = (periodicity) =>
  emits("update:periodicity", periodicity);
</script>

<template>
  <section class="periodicity">
    <span
      :class="periodicity === 'monthly' ? 'periodicity--ativo' : null"
      @click.native="updatePeriodicity('monthly')"
    >
      Monthly
    </span>
    <span
      :class="periodicity === 'yearly' ? 'periodicity--ativo' : null"
      @click.native="updatePeriodicity('yearly')"
    >
      Yearly
    </span>
  </section>
</template>

<style lang="scss" scoped>
.periodicity {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  gap: 1rem;
  border-radius: 10px;
  background-color: var(--magnolia);

  span {
    color: var(--cool-gray);
    font-weight: 500;

    &.periodicity--ativo {
      color: var(--marine-blue);    
    }
  }
}
</style>
