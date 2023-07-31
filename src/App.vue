<script setup>
import StoreHeader from './components/StoreHeader.vue'
import ProductList from './components/ProductList.vue'
import ProductCard from './components/ProductCard.vue'
import CartSection from './components/CartSection.vue'
import { ref } from 'vue'

const products = ref([
  {id: 0, image: "/src/assets/phone-photos-squared/case_1_pattern.jpg", name: "Black Pattern Case", desc: "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.", price: 2.99},
  {id: 1, image:"/src/assets/phone-photos-squared/case_cream.jpg", name: "Cream Case", desc: "Quisque vitae varius ex, eu volutpat orci.", price: 2.99},
  {id: 2, image:"/src/assets/phone-photos-squared/headphones_1.jpg", name: "Headphones", desc: "Duis ac nulla varius diam ultrices rutrum.", price: 29.99},
  {id: 3, image:"/src/assets/phone-photos-squared/octo_tripod_1.jpg", name: "Octo Tripod", desc: "Cras erat dui, finibus vel lectus ac, pharetra dictum odio.", price: 19.99}
])

// store products added to cart
const cart_items = ref([])
function addToCart(product) {
  cart_items.value.push(product)
}

// check if user is on cart page
const cart_open = ref(false)
function setCartOpen() {
  cart_open.value = !cart_open.value // sets to true, not false
}

// go back to homepage
function toHome() {
  cart_open.value = false
}

const product_id = ref(0)
// gets the product id
function getId(id) {
  product_id.value = id
}

</script>

<template>
  <div class="app">
    <StoreHeader
      :cart-items="cart_items"
      @set-cart-open="setCartOpen()"
      @to-home="toHome()"
    />
    <main class="main" v-if="!cart_open">
      <ProductCard
        :product-list="products"
        :product-id="product_id"
        @add-to-cart="(prod) => addToCart(prod)"
      />
      <ProductList
        :product-list="products"
        @get-id="(id) => getId(id)"
      />
    </main>
    <CartSection
      :cart-items="cart_items"
      v-else
    />
  </div>
</template>

<style scoped>
  .main {
    padding: 2em 4em;
  }
  @media only screen and (min-width: 600px) {

    /* using inheritance */
    /* change only font-size of parent and properties with em units are auto adjusted */
    .main {
      padding: 1em 8em;
    }
    .header {
      font-size: 0.9rem;
    }
    .main:deep(.prods) {
      font-size: 1rem;
    }
    .main:deep(.product-list-container) {
      font-size: 1rem;
    }
  }

  @media only screen and (min-width: 768px) {    
    /* >>> and /deep/ are deprecated, */
    /* change to :deep() */
    .header {
      font-size: 0.9rem;
    }
    .main {
      padding: 1.5em 14em;
    }
    .main:deep(.product-list-container) {
			font-size: 1.2rem;
    }
    .main:deep(.prods) {
      font-size: 1rem;
    }
  }

  @media only screen and (min-width: 992px) {
    .header {
      font-size: 1rem;
    }
    .main {
      display: flex;
      align-items: center;
      justify-content: space-evenly;
      padding: 3em;
    }
    /* take up 30% of .main */
    .main:deep(.product-list-container) {
			font-size: 1rem;
			width: 30%;
    }
    /* take up 65% of .main */
    .main:deep(.prods) {
      width: 65%;
      display: flex;
      font-size: 1.1rem;
      margin-bottom: 0;
    }
    /* same fixed for every image in .prods */
    .main:deep(.product-image) {
      width: 350px;
      height: 350px;
    }
    .main:deep(.product-details) {
      width: 100%;
    }
    /* change layout for button */
    /* see ProductCard for .atc and .atc-big btn */
    .main:deep(.atc) {
      display: none;
    }
    .main:deep(.atc-big) {
      background: #222;
      color: white;
      font-weight: bold;
      padding: 0.8em;
      width: 100%;
      display: inline-block;
      font-size: 1em;
      margin-top: auto;
    }
  }

  @media only screen and (min-width: 1200px) {
    .main {
      padding: 3em 5em;
    }
    .main:deep(.prods) {
      font-size: 1.3rem;
    }
    .main:deep(.product-list-container) {
			font-size: 1.3rem;
    }
  }

</style>
