<script setup>

</script>

<template>
  <header class="header">
    <h1 class="logo">PhoneX</h1>
    <a href="#" class="cart">
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
    font-size: 1.5em;
  }
  .cart {
    display: inline-block;
  }
  .cart-icon {
    width: 1.5em;
  }
</style>
