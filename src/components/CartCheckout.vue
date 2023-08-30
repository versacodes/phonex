<script setup>
import BaseInput from './BaseInput.vue'
</script>

<template>
  <section :class="$style['checkout-section']">
    <h1 :class="$style.title">Checkout Form</h1>
    <form
      :class="$style['cart-checkout']"
      method="post"
      action=""
      id="checkout-form"
    >
      <BaseInput
        label="Email: "
        placeholder="Enter your email"
        id="email"
        type="email"
        :class="$style.input"
        required
      />
      <BaseInput
        label="Full Name: "
        placeholder="Enter your full name"
        id="full-name"
        type="text"
        :class="$style.input"
        required
      />
      <BaseInput
        label="Card Number: "
        placeholder="Enter your Card Number"
        id="card-number"
        type="text"
        :class="$style.input"
        required
      />
      <BaseInput
        label="Expiration of Card: "
        placeholder="ex. 06/27"
        id="expiration-date"
        type="text"
        :class="$style.expiration"
        required
      />
      <BaseInput
        label="CVV: "
        placeholder="ex. 432"
        id="security-code"
        type="text"
        :class="$style.cvv"
        required
      />
    </form>
    <button
      :class="$style.button"
      form="checkout-form"
    >Submit</button>
  </section>
</template>


<style module>
.checkout-section {
  max-width: 450px;
  margin: 2rem auto;
  border: 1px solid #000;
  border-radius: 10px;
}

.title {
  text-align: center;
  color: #333;
  margin-top: 1.8rem;
  font-size: 1.8rem;
}

.cart-checkout {
  padding: 2rem;
}

.button {
  padding: 1em;
  font-size: 1rem;
  font-weight: bold;
  color: white;
  background: #222;
  width: 100%;
  border-radius: 0 0 8px 8px;  
}

.input {
  width: 100%;
  display: block;
}
</style>

