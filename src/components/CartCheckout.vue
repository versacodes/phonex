<script setup>
import { ref, toRaw, computed } from 'vue'

const props = defineProps({
  cart_items: Array
})

const item_array = props.cart_items

function deleteItem(id) {
  // remove only the given specific item 
  props.cart_items.splice(id, 1)
}

// returns a total number, then keep 2 decimal places only, then converts to Number
// toFixed() returns a string
const total_price = computed(() => {
  return Number((item_array.reduce((total, item) => total + item.price, 0)).toFixed(2))
})

</script>


<template>
  <div class="cart-checkout">
    <h2 class="cart-title">Cart Items</h2>
    <div class="item" v-for="(item, idx) in item_array" v-if="cart_items.length > 0" :key="item.id">
      <img class="item-image" :src="item.image" />
      <h6 class="item-name">
        {{ item.name }}
        <span class="item-quantity">{{ "x" + 1 }}</span>
      </h6>
      <p class="item-price">{{ "$" + item.price }}</p>
      <button class="delete" @click="deleteItem(idx)">X</button>
    </div>
  </div>
  <section class="fixed">
    <div class="total">
      <div class="total-names">
        <h6 class="total-product-price">Total Product Price</h6>
        <h6 class="shipping">Shipping Fee</h6>
        <h6 class="total-price">Total Price</h6>
      </div>
      <div class="total-prices">
        <h6 class="total-product-price">{{ "$"+total_price }}</h6>
        <h6 class="shipping">{{ "$"+2.99 }}</h6>
        <h6 class="total-price">{{ "$"+(total_price + 2.99) }}</h6>
      </div>
    </div>
    <button class="checkout-btn">CHECKOUT</button>
  </section>
</template>


<style scoped>
  .cart-checkout {
    /* center component */
    display: grid;
    place-items: center;
    background: #fdf;
    padding: 20px 0;
    margin-bottom: 7em;
  }
  .cart-title {
    margin-bottom: 20px;
    color: #242424;
  }
  .item {
    display: flex;
    align-items: center;
    background: #fafada;
    width: 70%;
    padding: 0.5em;
  }
  .item-image {
    flex-basis: 25%;
  }
  .item-name {
    margin-left: 10px;
    font-size: 0.7em;
    flex: 1;
    color: #222222;
    display: flex;
    flex-direction: column;
  }
  .item-quantity {
    font-size: 0.8em;
    margin-top: 5px;
    display: block;
    color: #444;
  }
  .item-price {
    margin-left: auto;
    margin-right: 15px;
    font-size: 0.5em;
    font-weight: bold;
  }
  .delete {
    background: #c44;
    width: 2em;
    height: 2em;
    font-size: 0.7em;
    margin-right: 10px;
    color: white;
    border-radius: 50%;
  }
  .delete:hover {
    box-shadow: 1px 1px 7px 0 black;
  }
  
  /* contains .total and .checkout-btn */
  .fixed {
    position: fixed;
    bottom: 0;
    width: 100%;
  }
  .total {
    background: #eedfed;
    padding: 1em 2em;
    display: flex;
    justify-content: space-between;
  }
  .total-names, .total-prices {
    font-size: 0.9em;
  }
  .total-product-price ~ h6 {
    margin-top: 0.5em;
  }
  .checkout-btn {
    background: #e33;
    width: 100%;
    padding: 1em;
    color: #fff;
    font-size: 0.8em;
    font-weight: bold;
  }
</style>









