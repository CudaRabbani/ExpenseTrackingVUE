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
//<script>
// VueJS@2.0 way using the OptionsAPI
// export default {
//     data() {
//         return {
//             transactions: [
//                 {id: 1, text: 'Flower', amount: -19.99},
//                 {id: 2, text: 'Fruits', amount: -29.99},
//                 {id: 3, text: 'Vegetables', amount: -9.99},
//                 {id: 4, text: 'Books', amount: -39.99},
//                 {id: 5, text: 'Salary', amount: 200.00}
//             ],
//         }
//     }
// }

//VueJS @3.0 using the CompositionAPI
// export default {
//     setup() {
//         const transactions = [
//                 {id: 1, text: 'Flower', amount: -19.99},
//                 {id: 2, text: 'Fruits', amount: -29.99},
//                 {id: 3, text: 'Vegetables', amount: -9.99},
//                 {id: 4, text: 'Books', amount: -39.99},
//                 {id: 5, text: 'Salary', amount: 200.00}
//             ];
        
//         return {
//             transactions
//         }
//     }
// }
// </script>

<script setup>
const transactions = [
        {id: 1, text: 'Flower', amount: -19.99},
        {id: 2, text: 'Fruits', amount: -29.99},
        {id: 3, text: 'Vegetables', amount: -9.99},
        {id: 4, text: 'Books', amount: -39.99},
        {id: 5, text: 'Salary', amount: 200.00}
    ];

</script>