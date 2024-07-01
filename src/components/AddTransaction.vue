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

const text = ref('');
const amount = ref('');

const onSubmit = () => {};
</script>
