<template>
  <Header />

  <div class="container">
    <Balance :total="+total" />
    <IncomeExpenses :income="+income" :expenses="+expenses" />
    <TransactionList
      :transactions="transactions"
      @transactionDeleted="handleTransactionDeleted"
    />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import { useToast } from 'vue-toastification';

import { ref, computed } from 'vue';
const toast = useToast();
const transactions = ref([
  {
    id: 1,
    text: 'Flower',
    amount: 15.02,
  },
  {
    id: 2,
    text: 'Book',
    amount: 130,
  },
  {
    id: 3,
    text: 'Food',
    amount: 8,
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

//ADD TRANSACTION
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });
  toast.success('Transaction added successfully');
};
//UNIQUE IDs
const generateUniqueId = () => {
  return Math.floor(Math.random() * 100000);
};

//DELETE TRANSACTIONS
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  toast.success('Transaction deleted successfully');
};
</script>
