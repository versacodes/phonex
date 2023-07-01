<script setup>

const props = defineProps({
  product_list: Array
})

</script>

<template>
  <!-- <div class="product-card"> -->
  <div class="prods">
    <img src="/src/assets/phone-photos-squared/headphones_1.jpg" alt="insert image here" class="product-image" />
    <div class="product-details">
      <h1 class="product-name">Product Name</h1>
      <h4 class="product-price">$9.99</h4>
      <p class="product-desc">Nullam tempus scelerisque purus, sed mattis elit condimentum nec. Proin ipsum purus, laoreet quis dictum a, laoreet sed ligula.</p>
      <button class="atc-big">Add To Cart</button>
    </div>
    <!-- transfer button inside .prod instead of .product_details -->
    <button class="atc">Add To Cart</button>
  </div>
  <!-- </div> -->
</template>

<style scoped>
  /* .product-card { */
  /*   font-size: 0.9rem; */
  /*   /* background: #efefef; */ 
  /*   /* add whitespace between ProductCard and ProductList */ 
  /*   /* margin-bottom: 15px; */ 
  /* } */
  .prods {
    /* display: flex; */
    background: #efefef;
    margin-bottom: 15px;
  }
  .product-details {
    padding: 1em;
    display: flex;
    flex-direction: column;
  }
  
  .product-image {
  }
  
  .product-name {
    font-size: 1.4em;
    margin-bottom: 0.2em;
  }
  .product-price {
    margin-bottom: 1.2em;
    font-size: 0.9em;
    color: #333333;
  }
  .product-desc {
    font-size: 0.8em;
    margin-bottom: 1em;
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
  }
  .atc-big {
    display: none;
  }
  
</style>
