<script setup>
import { ref, shallowRef } from "vue";
import Header from "../base/Header.vue";
import SelectableCard from "../base/SelectableCard.vue";
import PeriodicitySelect from "../base/PeriodicitySelect.vue";

const plans = shallowRef([
  { id: 1, plan: "arcade", monthly: { value: 9 }, yearly: { value: 90 } },
  { id: 2, plan: "advanced", monthly: { value: 12 }, yearly: { value: 120 } },
  { id: 3, plan: "pro", monthly: { value: 15 }, yearly: { value: 150 } },
]);

const periodicity = ref("monthly");
</script>

<template>
  <section class="wrapper-select-plan">
    <Header
      title="Select your plan"
      subtitle="You have the option of monthly or yearly billing."
    />
    <section class="wrapper-select-plan__plans">
      <SelectableCard
        v-for="plan of plans"
        :key="plan.id"
        :periodicity="periodicity"
        :plan="plan"
      />
    </section>
    <PeriodicitySelect
      :periodicity="periodicity"
      @update:periodicity="periodicity = $event"
    />
  </section>
</template>

<style lang="scss" scoped>
.wrapper-select-plan {
  &__plans {
    display: grid;
    justify-content: space-between;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}
</style>
