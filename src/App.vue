<script setup>
import StoreHeader from './components/StoreHeader.vue'
import ProductList from './components/ProductList.vue'
import ProductCard from './components/ProductCard.vue'


</script>

<template>

  <StoreHeader />
  <main class="main">
    <ProductList />
    <ProductCard />
  </main>

</template>

<style scoped>
.main {
  display: flex;
}
.main > * {
  flex: 1 1 100%;
}
</style>
