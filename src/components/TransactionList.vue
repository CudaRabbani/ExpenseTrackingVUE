<template>
    <h1>History</h1>
    <ul id="list" class="list">
        <li 
        v-for="transaction of transactions"
        :key="transaction.id"
        :class="transaction.amount < 0 ? 'minus' : 'plus' ">
            {{ transaction.text }} <span>${{ transaction.amount }}</span>
            <button class="delete-btn">X</button>
        </li>
    </ul>
</template>
<script setup>
    import {defineProps} from 'vue';

    const props = defineProps({
        transactions: {
            type: Array,
            required: true,
        },
    });
</script>