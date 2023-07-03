<script setup>
import StoreHeader from './components/StoreHeader.vue'
import ProductList from './components/ProductList.vue'
import ProductCard from './components/ProductCard.vue'
import AppDesktopSize from './components/AppDesktopSize.vue'
import { ref, onMounted } from 'vue'

const products = ref([
  {id: 0, image: "/src/assets/phone-photos-squared/case_1_pattern.jpg", name: "Black Pattern Case", desc: "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.", price: 2.99},
  {id: 1, image:"/src/assets/phone-photos-squared/case_cream.jpg", name: "Cream Case", desc: "Quisque vitae varius ex, eu volutpat orci.", price: 2.99},
  {id: 2, image:"/src/assets/phone-photos-squared/headphones_1.jpg", name: "Headphones", desc: "Duis ac nulla varius diam ultrices rutrum.", price: 29.99},
  {id: 3, image:"/src/assets/phone-photos-squared/octo_tripod_1.jpg", name: "Octo Tripod", desc: "Cras erat dui, finibus vel lectus ac, pharetra dictum odio.", price: 19.99}
])

const product_id = ref(0)
function getId(id) {
  product_id.value = id
}

</script>

<template>
  <div class="app">
    <StoreHeader />
    <main class="main">
      <ProductCard :product_list="products" :prod_id="product_id"/>
      <ProductList :product_list="products" :get_id="getId"/>
    </main>
  </div>

</template>

<style scoped>
  /* padding for whitespace */
  .app {
    height: 100vh;
  }
  .main {
    padding: 0.6em 4em;
    height: 100%;
  }
  @media only screen and (min-width: 600px) {

    /* using inheritance */
    /* change only font-size of parent and properties with em units are auto adjusted */
    .main {
      padding: 1em 8em;
    }
    .header {
      font-size: 0.9rem;
    }
    .main:deep(.prods) {
      font-size: 1rem;
    }
    .main:deep(.product-list-container) {
      font-size: 1.5rem;
    }
  }

  @media only screen and (min-width: 768px) {    
    /* >>> and /deep/ are deprecated, */
    /* change to :deep() */
    .header {
      font-size: 0.9rem;
    }
    .main {
      padding: 1.5em 14em;
    }
    .main:deep(.product-list-container) {
			font-size: 1.6rem;
    }
    .main:deep(.prods) {
      font-size: 1rem;
    }
  }

  @media only screen and (min-width: 992px) {
    .header {
      font-size: 1rem;
    }
    .main {
      display: flex;
      align-items: center;
      justify-content: space-evenly;
      padding: 3em;
    }
    /* take up 30% of .main */
    .main:deep(.product-list-container) {
			font-size: 1.8rem;
			width: 30%;
    }
    /* take up 65% of .main */
    .main:deep(.prods) {
      width: 65%;
      display: flex;
      font-size: 1.1rem;
      margin-bottom: 0;
    }
    /* same fixed for every image in .prods */
    .main:deep(.product-image) {
      width: 350px;
      height: 350px;
    }
    .main:deep(.product-details) {
      width: 100%;
    }
    /* change layout for button */
    /* see ProductCard for .atc and .atc-big btn */
    .main:deep(.atc) {
      display: none;
    }
    .main:deep(.atc-big) {
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

  @media only screen and (min-width: 1200px) {
    .main {
      padding: 3em 5em;
    }
    .main:deep(.prods) {
      /* width: 100%; */
      font-size: 1.3rem;
    }
    .main:deep(.product-list-container) {
			font-size: 1.9rem;
    }
  }

</style>
