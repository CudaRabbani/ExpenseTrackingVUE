<template>
    <h3>Add new transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" v-model="text" placeholder="Enter text ...">
        </div>
        <div class="form-control">
            <label for="text">Amount <br />
            (negative - expense, positive - income)</label>
            <input type="string" id="amount" v-model="amount" placeholder="Enter amount ...">
        </div>
        <button class="btn">Add transaction</button>
    </form>
</template>
<script setup>
import {ref} from 'vue';
import {useToast} from 'vue-toastification';

const text = ref('');
const amount = ref('');

const toast = useToast();
//creating custom event
const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error('Both field must be filled out');
        return;
    }

    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value)
    }

    emit('transactionSubmitted', transactionData);
    console.log(text.value, amount.value);
    text.value = '';
    amount.value = '';
}
</script>