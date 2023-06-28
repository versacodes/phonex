<script setup>
import StoreHeader from './components/StoreHeader.vue'
import ProductList from './components/ProductList.vue'
import ProductCard from './components/ProductCard.vue'
import { ref } from 'vue'

const products = ref([
  {id: 0, image: "/src/assets/phone-photos-squared/case_1_pattern.jpg", name: "Black Pattern Case", desc: "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas."},
  {id: 1, image:"/src/assets/phone-photos-squared/case_cream.jpg", name: "Cream Case", desc: "Quisque vitae varius ex, eu volutpat orci."},
  {id: 2, image:"/src/assets/phone-photos-squared/headphones_1.jpg", name: "Headphones", desc: "Duis ac nulla varius diam ultrices rutrum."},
  {id: 3, image:"/src/assets/phone-photos-squared/octo_tripod_1.jpg", name: "Octo Tripod", desc: "Cras erat dui, finibus vel lectus ac, pharetra dictum odio."}
])


</script>

<template>

  <StoreHeader />
  <main class="main">
    <ProductCard :product_list="products"/>
    <ProductList :product_list="products"/>
  </main>

</template>

<style scoped>
  .main {
    padding: 0.5em 4em;
  }
  
  @media only screen and (min-width: 600px) {

    /* using inheritance */
    /* change only font-size of parent and properties with em units are auto adjusted */
    .main {
      padding: 0.5em 8em;
    }
    .header {
      font-size: 1.3rem;
    }
    .product-card {
      font-size: 1.4rem;
    }
    .product-list-container {
      font-size: 1.8rem;
    }
  }

  @media only screen and (min-width: 768px) {
    .main {
      padding: 0.5em 10em;
    }
    .header {
      font-size: 1.4rem;
    }
    .product-card {
      font-size: 1.6rem;
    }
    .product-list-container {
      font-size: 2.4rem;
    }
  }

</style>
