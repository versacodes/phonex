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
    <div class="product-preview" v-for="product in products" key="product.id">
      <img class="product-list-image" :src="product.image" :alt="alt" />
      <h2 class="product-name">{{product.name}}</h2>
    </div>
  </div>
</template>

<style scoped>
  .product-list-container {
    background: #eee;
    padding: 1em 1em;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px 50px;
  }
  .product-preview {
    background: #444;
    width: 30%;
    /* flex: 40%; */
  }
  .product-list-image {
    /* width: 50%; */
  }
  .product-name {
    font-size: 0.8em;
    text-align: center;
    padding: 1em;
    color: white;
    margin-top: auto;
    /* margin-bottom: auto; */
  }
</style>
