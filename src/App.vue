<template>
  <Header />
  <div class="container">
    <Balance :total="total" />
    <IncomeExpense :income="income" :expense="expense"/>
    <TransactionList :transactions="transactions"/>
    <AddTransaction @transactionSubmitted="handleTransactions"/>
  </div>
</template>
<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomExpense from './components/IncomeExpense.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import {useToast} from 'vue-toastification';

import {ref, computed} from 'vue';

const toast = useToast();
const transactions = ref([
        {id: 1, text: 'Flower', amount: -19.99},
        {id: 2, text: 'Fruits', amount: -29.99},
        {id: 3, text: 'Vegetables', amount: -9.99},
        {id: 4, text: 'Books', amount: -39.99},
        {id: 5, text: 'Salary', amount: 200.00}
    ]);

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0).toFixed(2);
});

const income = computed(() => {
  return transactions.value
  .filter((transaction) => transaction.amount > 0)
  .reduce((acc, income) => acc+income.amount, 0).toFixed(2);
});

const expense = computed(() => {
  return transactions.value
  .filter((transaction) => transaction.amount < 0)
  .reduce((acc, income) => acc+income.amount, 0).toFixed(2);
});

const handleTransactions = (transactionData) => {
  const lastTrans = transactions.value[transactions.value.length - 1];
  transactions.value.push({
    id: ++lastTrans.id,
    text: transactionData.text,
    amount: transactionData.amount
  });
  toast.success('Transaction is added');
}
</script>
