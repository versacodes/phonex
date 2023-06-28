<script setup>
import { ref } from 'vue';

// transfer 'products' to App.vue to use as props for children components
const products = ref([
  {id: 0, image: "/src/assets/phone-photos-squared/case_1_pattern.jpg", name: "Black Pattern Case", desc: "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas."},
  {id: 1, image:"/src/assets/phone-photos-squared/case_cream.jpg", name: "Cream Case", desc: "Quisque vitae varius ex, eu volutpat orci."},
  {id: 2, image:"/src/assets/phone-photos-squared/headphones_1.jpg", name: "Headphones", desc: "Duis ac nulla varius diam ultrices rutrum."},
  {id: 3, image:"/src/assets/phone-photos-squared/octo_tripod_1.jpg", name: "Octo Tripod", desc: "Cras erat dui, finibus vel lectus ac, pharetra dictum odio."}
])

const alt = ref("Hello")
</script>

<template>
  <div class="product-list-container">
    <!-- loop over products then render .product-preview based on key values -->
    <div class="product-preview" v-for="product in products" key="product.id">
      <img class="product-list-image" :src="product.image" :alt="product.name" />
      <h2 class="product-name">{{product.name}}</h2>
    </div>
  </div>
</template>

<style scoped>
  .product-list-container {
    /* background: #eee; */
    padding: 0.5em 0.5em;
    display: flex;
    justify-content: center;
    /* flex-wrap: wrap; */
  }
  .product-preview ~ .product-preview {
    /* margin-top: 6px; */
  }
  .product-preview {
    background: #444;
  }
  
  .product-list-image {
    width: 80px;
    height: 80px;
  }
  
  .product-name {
    font-size: 0.7em;
    text-align: center;
    padding: 1em;
    color: white;
    margin-top: auto;
    /* margin-bottom: auto; */
  }
  .product-desc {
    font-size: 0.7em;
    color: white;
  }
</style>
