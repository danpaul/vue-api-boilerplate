<script setup>
import { RouterView, RouterLink } from "vue-router";
</script>

<template>
  <main class="container">
    <nav>
      <ul>
        <li><strong>Bill's Bank and Used Car Sales</strong></li>
      </ul>
      <ul>
        <li>
          <RouterLink to="/">Home</RouterLink>
        </li>
        <li>
          <RouterLink to="/api-test">API Test</RouterLink>
        </li>
      </ul>
    </nav>
    <RouterView></RouterView>
  </main>
</template>

<style scoped></style>
