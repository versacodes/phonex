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
      <section>
        <h2 class="product-name">{{product.name}}</h2>
      </section>  
    </div>
  </div>
</template>

<style scoped>
  .product-list-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    background: #888;
    padding: 0.8em;
  }
  
  .product-preview {
    background: #444;
    /* 2 products per row */
    /* 45% to accomodate for extra whitespace */
    width: 45%;
  }

  .product-preview:first-child, .product-preview:nth-child(2) {
    margin-bottom: 10px;
  }  

  .product-preview:nth-child(2), .product-preview:last-child {
    margin-left: 10px;
  }
  
  .product-name {
    font-size: 0.5em;
    text-align: center;
    padding: 1em;
    color: white;
    /* break long word into multiple lines */
    overflow-wrap: break-word;
  }
</style>
