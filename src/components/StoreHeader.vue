<script setup>

const props = defineProps({
  cart_items: Array
})

</script>

<template>
  <header class="header">
    <h1 class="logo">PhoneX</h1>
    <a href="#" class="cart">
      <div class="circle">{{ cart_items.length }}</div>
      <img src="../assets/cart_icon.png" class="cart-icon">
    </a>
  </header>
</template>

<style scoped>
  .header {
    background: #333;
    display: flex;
    padding: 1em 2em;
    justify-content: space-between;
    align-items: center;
    color: white;
  }
  .logo {
    font-size: 1.1em;
  }
  .cart {
    display: inline-block;
    position: relative;
  }
  .cart-icon {
    width: 1.5em;
  }
  /* circle notif for cart items */
  .circle {
    background: #54c;
    width: 1.5em;
    height: 1.5em;
    font-size: 0.8em;
    border-radius: 50%;
    text-align: center;
    display: grid;
    place-items: center;
    position: absolute;
    right: -1em;
    top: -0.5em;
  }
</style>
