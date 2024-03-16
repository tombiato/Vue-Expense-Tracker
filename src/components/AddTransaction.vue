<script setup>
import {ref} from "vue";
import {useToast} from "vue-toastification";

const text = ref('');
const amount = ref(0);

const emit = defineEmits(['transactionSubmitted']);

const toast = useToast();
const onSubmit = () => {
  if (text.value.trim() === '' || amount.value === 0) {
    toast.error('Please enter a valid text and amount');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: amount.value
  }

  emit('transactionSubmitted', transactionData);

  text.value = '';
  amount.value = 0;
}
</script>

<template>
  <h3>Add new transaction</h3>
  <form id="form"
        @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input id="text"
             v-model="text"
             placeholder="Enter text..."
             type="text" />
    </div>
    <div class="form-control">
      <label for="amount"
      >Amount <br />
        (negative - expense, positive - income)</label
      >
      <input id="amount"
             v-model="amount"
             placeholder="Enter amount..."
             type="number" />
    </div>
    <button class="btn">Add transaction</button>
  </form>
</template>

<style scoped>

</style>
