<template>
  <Header />

  <div class="container">
    <Balance />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';

export default {
  components: {
    Header,
    Balance,
    AddTransaction,
    TransactionList,
    IncomeExpenses,
  },
};
</script>
