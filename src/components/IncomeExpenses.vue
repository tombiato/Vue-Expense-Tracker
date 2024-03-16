<script setup>
const props = defineProps({
  incomes: {
    type: Number,
    required: true
  },
  expenses: {
    type: Number,
    required: true
  }
})
</script>

<template>
  <div class="inc-exp-container">
    <div>
      <h4>Income</h4>
      <p id="money-plus"
         class="money plus">+{{ incomes }}</p>
    </div>
    <div>
      <h4>Expense</h4>
      <p id="money-minus"
         class="money minus">-${{ expenses }}</p>
    </div>
  </div>
</template>

<style scoped>

</style>
