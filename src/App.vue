<script setup>
import StoreHeader from './components/StoreHeader.vue'
import ProductList from './components/ProductList.vue'
import ProductCard from './components/ProductCard.vue'


</script>

<template>

  <StoreHeader />
  <main class="main">
    <ProductCard />
    <ProductList />
  </main>

</template>

<style scoped>
  .main {
    padding: 0.5em 4em;
  }
  @media only screen and (min-width: 600px) {
    .main {
      padding: 0.5em 10em;
    }
    .product-card {
      font-size: 1.5rem;
    }
  }

</style>
