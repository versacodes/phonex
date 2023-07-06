<script setup>
import { ref, toRaw } from 'vue'

const props = defineProps({
  cart_items: Array
})

const item_array = toRaw(props.cart_items)

function deleteItem(id) {
  props.cart_items.splice(id, 1)
}

</script>


<template>
  <div class="cart-checkout">
    <h2 class="cart-title">Cart Items</h2>
    <div class="item" v-for="(item, idx) in item_array" v-if="cart_items.length > 0" :key="item.id">
      <img class="item-image" :src="item.image" />
      <h4 class="item-name">
        {{ item.name }}
        <span class="item-quantity">{{ "x" + 1 }}</span>
      </h4>
      <p class="item-price">{{ "$" + item.price }}</p>
      <button class="delete" @click="deleteItem(idx)">X</button>
    </div>
  </div>
  <button class="checkout-btn">CHECKOUT</button>
</template>


<style scoped>
  .cart-checkout {
    /* center component */
    display: grid;
    place-items: center;
    background: #fdf;
    padding: 20px 0;
    margin-bottom: 4em;
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
  .checkout-btn {
    background: #e33;
    width: 100%;
    padding: 1em;
    color: #fff;
    position: fixed;
    bottom: 0;
    font-size: 1.1em;
    font-weight: bold;
  }
</style>

