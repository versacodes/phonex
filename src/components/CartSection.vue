<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  cart_items: Array
})

function deleteItem(id) {
  // remove only the given specific item 
  props.cart_items.splice(id, 1)
}

const filtered_items = computed(() => {
  return props.cart_items.reduce((acc, item) => {
    // skip if el in item by name property
    if(acc.some(el => el.name === item.name)) {
      return acc // continue next iter
    }
    acc.push(item)
    return acc
  }, [])
})

// show shipping fee only if there is item in cart
const shipping_fee = computed(() => {
  return props.cart_items.length > 0 ? 2.99 : 0
})

// returns a total number, then keep 2 decimal places only, then converts to Number
// toFixed() returns a string
const total_price = computed(() => {
  return Number((props.cart_items.reduce((total, item) => total + item.price, 0)).toFixed(2))
})

// user reduce to return an object with values of how many times were an item listed to the cart once or more times
const quantityComputed = computed(() => {
  return props.cart_items.reduce((acc, item) => {
    if(item.name in acc) {
      acc[item.name] += 1
      return acc
    }
    acc[item.name] = 1
    return acc //returns object
  }, {})
})


</script>


<template>
  <div class="cart-checkout">
    <h2 class="cart-title">Cart Items</h2>
    <template
      v-if="cart_items.length !== 0"
    >
      <div
        class="item"
        v-for="(item, idx) in filtered_items"
        :key="item.id"
      >
        <img
          class="item-image"
          :src="item.image"
        />
        <h6 class="item-name">
          {{ item.name }}
          <span class="item-quantity">{{ "x" + quantityComputed[item.name] }}</span>
        </h6>
        <p class="item-price">{{ "$" + item.price }}</p>
        <button
          class="delete"
          @click="deleteItem(idx)"
        >X</button>
      </div>
    </template>
  <!-- show message if cart is empty -->
  <p
    class="empty-cart-message"
    v-else
  >Your cart is empty.</p>
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
        <h6 class="shipping">{{ "$"+ shipping_fee }}</h6>
        <h6 class="total-price">{{ "$"+(total_price + shipping_fee).toFixed(2) }}</h6>
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
    padding: 20px 0;
    margin-bottom: 8rem;
  }
  .cart-title {
    margin-bottom: 20px;
    color: #242424;
  }
  .item {
    display: flex;
    align-items: center;
    /* background: #fafada; */
    border: 1px solid #222;
    width: 70%;
    padding: 0.5em;
    margin-bottom: 1px;
  }
  .item-image {
    width: 15%;
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
    display: flex;
    justify-content: space-between;
    background: #eedfed;
    padding: 1em 2em;
  }
  .total-names, .total-prices {
    font-size: 0.9em;
  }
  .total-product-price ~ h6 {
    margin-top: 0.5em;
  }
  .total-price {
    font-size: 0.9em;
  }
  .checkout-btn {
    background: #e33;
    color: #fff;
    width: 100%;
    padding: 1em;
    font-size: 0.8em;
    font-weight: bold;
  }
  .empty-cart-message {
    /* background: #8cc; */
    /* display: flex; */
    margin-top: 5.5rem;
    font-size: 1rem;
    color: #555;
  }
</style>









