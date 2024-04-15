<script setup>
defineProps({
  transactions: Array,
});
</script>

<template>
  <h2>Transactions:</h2>
  <table>
    <thead>
      <tr>
        <th scope="col">From</th>
        <th scope="col">To</th>
        <th scope="col">Amount</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="transaction in transactions">
        <td>{{ transaction.from }}</td>
        <td>{{ transaction.to }}</td>
        <td>{{ transaction.amount }}</td>
      </tr>
    </tbody>
  </table>
</template>
