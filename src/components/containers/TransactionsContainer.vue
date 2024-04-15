<script setup>
import Loading from "../common/Loading.vue";
import TransactionsTable from "../common/TransactionsTable.vue";
import { useQueryClient, useQuery, useMutation } from "@tanstack/vue-query";

/**
 * IMPORTANT! This is a demo file to show the basic pattern of using
 *  Vue Query to make requests to your API. You likely want to organzie
 *  these better, i.e. putting queries and mutations in their own
 *  files inside a /query directory so that they can potentially
 *  be reused between different components.
 */

// demo data, this would normally come from the API
let transactions = [
  {
    to: "AZ77VTBA00000000001234567890",
    from: "BY86AKBB10100000002966000000",
    amount: 3.33,
  },
  {
    to: "AZ77VTBA00000000001234567890",
    from: "BY86AKBB10100000002966000000",
    amount: 4.44,
  },
];

// Access QueryClient instance
const queryClient = useQueryClient();

// helper function to demo async functionality, this would normally happen during API requests
function timeout(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

// Query
const { isLoading, isError, data, error } = useQuery({
  queryKey: ["transactions"],
  queryFn: async () => {
    // pretend we're asynchronously calling the API here to get the data...
    await timeout(500);
    return transactions;
  },
});

// Mutation
// we can also check isLoading, isError, error fields on out mutation
const { mutate, isPending } = useMutation({
  mutationFn: async (data) => {
    // this data would normally get sent to the server here
    console.log("sending transaction to the API:", data);

    // pretend we're sending the new transaction data to the server
    await timeout(1000);

    // just for demo! we would normally just invalidate the query and
    // the client would refetch new data from the server
    transactions = [...transactions, data];
  },
  onSuccess: () => {
    // Invalidate the query so data gets refetched
    queryClient.invalidateQueries({ queryKey: ["transactions"] });
  },
});

function onButtonClick() {
  mutate({
    to: "AZ77VTBA00000000001234567890",
    from: "BY86AKBB10100000002966000000",
    amount: 5.55,
  });
}
</script>

<template>
  <span v-if="isLoading || isPending"><Loading /></span>
  <span v-else-if="isError">Error: {{ error.message }}</span>
  <!-- We can assume by this point that `isSuccess === true` -->
  <ul v-else-if="data.length">
    <TransactionsTable :transactions="data" />
    <button @click="onButtonClick">Add Transaction</button>
  </ul>
  <div v-else>There are no transactions!</div>
</template>
