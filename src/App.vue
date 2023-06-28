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
  /* display: flex; */
  padding: 0.5em 5.5em;
}
.main > .product-list-container {
  /* flex: 60%; */
}
</style>
