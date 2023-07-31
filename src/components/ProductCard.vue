<script setup>
import { computed } from 'vue'

const props = defineProps({
  productList: Array,
  productId: Number,
})

defineEmits(['addToCart'])

//should be computed, relies on reactive/ref data
const product = computed(() => {
  return props.productList[props.productId]
})
</script>

<template>
  <div class="prods">
    <img :src="product.image" :alt="product.name" class="product-image" />
    <div class="product-details">
      <h1 class="product-name">{{product.name}}</h1>
      <h4 class="product-price">{{"$" + product.price}}</h4>
      <p class="product-desc">{{product.desc}}</p>
      <button class="atc-big" @click="$emit('addToCart', product)">Add To Cart</button>
    </div>
    <!-- transfer button inside .prod instead of .product_details -->
  </div>
</template>

<style scoped>
  .prods {
    background: #efefef;
    margin-bottom: 15px;
  }
  .product-details {
    display: flex;
    flex-direction: column;
  }
  /* all children except for .atc-big */
  .product-details > :not(.atc-big) {
    margin-left: 1.5rem;
    margin-right: 1.5rem;
  }
  .product-name {
    font-size: 1.4em;
    margin-top: 1em;
    margin-bottom: 0.3em;
  }
  .product-price {
    font-size: 0.9em;
    color: #333333;
  }
  .product-desc {
    font-size: 0.8em;
    margin-bottom: 2.5em;
    margin-top: 1.5em;
    /* improve readability by adding spacing in desc */
    line-height: 1.5;
    letter-spacing: 0.6px;
    color: #343434;
  }
  .atc {
    background: #222;
    color: white;
    font-weight: bold;
    padding: 0.8em;
    width: 100%;
    display: inline-block;
    font-size: 1em;
    display: none;
  }
  .atc-big {
    background: #222;
    color: white;
    font-weight: bold;
    padding: 0.8em;
    width: 100%;
    display: inline-block;
    font-size: 1em;
    margin-top: auto;
    cursor: pointer;
  }
  
</style>
