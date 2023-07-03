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
      <h4 class="item-name">{{ item.name }}</h4>
      <p class="item-quantity">{{ "x" + 1 }}</p>
      <p class="item-price">{{ "$" + item.price }}</p>
      <button class="delete" @click="deleteItem(idx)">X</button>
    </div>
  </div>
</template>


<style scoped>
  .cart-checkout {
    display: grid;
    place-items: center;
  }
  .item {
    display: flex;
    align-items: center;
    /* justify-content: space-between; */
    background: #fcfefd;
    width: 70%;
    padding: 1em;
  }
  .item-image {
    width: 70px;
    height: 70px;
  }
  .item-name {
    margin-left: 15px;
  }
  .item-quantity {
    margin-left: 10px;
    font-size: 0.9em;
  }
  .item-price {
    margin-left: auto;
    margin-right: 15px;
    font-size: 0.9em;
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
  /* .form { */
  /*   padding: 1.5em; */
  /*   background: #ddd; */
  /* } */
  /* .email { */
  /*   font-size: 1.2em; */
  /*   display: block; */
  /*   margin-bottom: 8px; */
  /* } */
  /* .email-input { */
  /*   padding: 1em; */
  /*   border: 1px solid #555; */
  /* } */
</style>

