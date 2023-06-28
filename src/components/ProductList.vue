<script setup>
import { ref } from 'vue';

const props = defineProps({
  product_list: Array
})

</script>

<template>
  <div class="product-list-container">
    <!-- loop over products then render .product-preview based on key values -->
    <div class="product-preview" v-for="product in product_list" key="product.id">
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
  }
  
  .product-preview {
    background: #444;
    /* 2 products per row */
    /* 45% to accomodate for extra whitespace(see .product-preview below) */
    width: 45%;
  }
  
  .product-preview:first-child, .product-preview:nth-child(2) {
    margin-bottom: 10px;
  }  

  .product-preview:nth-child(2), .product-preview:last-child {
    margin-left: 10px;
  }

  .product-preview:hover {
    scale: 1.04;
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
