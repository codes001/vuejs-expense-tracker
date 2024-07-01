<template>
  <Header />

  <div class="container">
    <Balance :total="total" />
    <IncomeExpenses :income="+income" :expenses="+expenses" />
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
import { ref, computed } from 'vue';

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

//BALANCE SUM
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
  console.log(total);
});

// CALCULATE THE INCOME
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
});

//CALCULATE THE EXPENSES
const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});
</script>
