<script setup>
</script>

<template>
  <div class="product-card">
    <div class="prod">
      <img src="/src/assets/phone-photos-squared/headphones_1.jpg" alt="insert image here" class="product-image" />
      <div class="product-details">
        <h1 class="product-name">Product Name</h1>
        <h4 class="product-price">$9.99</h4>
        <p class="product-desc">Nullam tempus scelerisque purus, sed mattis elit condimentum nec. Proin ipsum purus, laoreet quis dictum a, laoreet sed ligula.</p>
      </div>
      <button class="atc">Add To Cart</button>
    </div>
  </div>
</template>

<style scoped>
  .product-card {
    width: 100%;
    font-size: 1rem;
    /* height: 100vh; */
    /* display: flex; */
    background: #ddd;
    margin-bottom: 10px;
  }
  .prod {
    width: 100%;
  }
  .product-details {
    padding: 1em;
    display: flex;
    flex-direction: column;
  }
  .product-image {
  }
  .product-name {
    font-size: 1.5em;
    margin-bottom: 5px;
  }
  .product-price {
    margin-bottom: 15px;
    font-size: 0.8em;
  }
  .product-desc {
    font-size: 0.8em;
    margin-bottom: 1em;
    line-height: 1.4;
    letter-spacing: 0.2px;
  }
  .atc {
    background: #222;
    color: white;
    padding: 1em;
    width: 100%;
  }
</style>
