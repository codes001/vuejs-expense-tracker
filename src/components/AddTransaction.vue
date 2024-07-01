<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input type="text" id="text" placeholder="Add here..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="amount">Amount <br /> </label>
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div>
    <button class="btn">Add</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const text = ref('');
const amount = ref('');
const emit = defineEmits(['transactionSubmitted']);
const toast = useToast();

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error('All fields are required');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };
  emit('transactionSubmitted', transactionData);
  //RESET ALL INOUT FIELDS
  text.value = '';
  amount.value = '';
};
</script>
