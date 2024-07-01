<template>
  <Header />

  <div class="container">
    <Balance />
    <IncomeExpenses />
    <TransactionList :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import { ref } from 'vue';

const transactions = ref([
  {
    id: 1,
    text: 'Flower',
    amount: -15.02,
  },
  {
    id: 2,
    text: 'Book',
    amount: 130,
  },
  {
    id: 3,
    text: 'Food',
    amount: -8,
  },
]);
</script>
