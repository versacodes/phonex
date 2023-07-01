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
  <div class="app">
    <StoreHeader />
    <main class="main">
      <ProductCard :product_list="products"/>
      <ProductList :product_list="products"/>
    </main>

    <main class="main-big">
      <ProductCard :product_list="products"/>
      <ProductList :product_list="products"/>
    </main>
  </div>

</template>

<style scoped>
  .app {
    /* background: #569; */
    /* height: 100vh; */
  }
  .main {
    padding: 0.6em 4em;
    height: 100%;
    background: #859;
  }
  .main-big {
    display: none;
  }

  @media only screen and (min-width: 600px) {

    /* using inheritance */
    /* change only font-size of parent and properties with em units are auto adjusted */
    .main {
      padding: 1em 8em;
    }
    .header {
      font-size: 1.3rem;
    }
    .main:deep(.prods) {
      font-size: 1.3rem;
    }
    .main:deep(.product-list-container) {
      font-size: 1.8rem;
    }
  }

  @media only screen and (min-width: 768px) {
    
    /* todos: */
    /*   - responsive design */
    /*   - refactor data using computed */
    /*   - use v-binding for certain classes */
    
    /* >>> and /deep/ are deprecated, */
    /* change to :deep() */
    .header {
      font-size: 1.2rem;
    }
    .main:deep(.product-list-container) {
			font-size: 2.5rem;
    }
    .main:deep(.product-preview) {
      width: 45%;
    }
    .main:deep(.prods) {
      /* width: 45%; */
      font-size: 1.5rem;
      /* margin-bottom: 0; */
    }
  }

  @media only screen and (min-width: 992px) {
    .header {
      font-size: 1.6rem;
    }
    .main {
      display: none;
    }
    .main-big {
      display: flex;
      align-items: center;
      height: 100vmin;
      justify-content: space-evenly;
    }
    .main-big:deep(.product-list-container) {
			width: 25%;
    }
    .main-big:deep(.product-preview) {
      width: 45%;
    }
    /* .main-big >>> .product-details { */
    /*   background: #745; */
    /* } */
    .main-big:deep(.prods) {
      width: 60%;
      display: flex;
      /* height: 100vmin; */
      font-size: 1em;
      margin-bottom: 0;
    }
    .main-big:deep(.atc) {
      display: none;
    }
    .main-big:deep(.atc-big) {
      /* display: none; */
      background: #222;
      color: white;
      font-weight: bold;
      padding: 0.8em;
      width: 100%;
      display: inline-block;
      font-size: 1em;
      margin-top: auto;
    }
  }

</style>
