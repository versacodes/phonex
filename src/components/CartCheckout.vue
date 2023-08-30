<script setup>
import BaseInput from './BaseInput.vue'
import { ref, computed } from 'vue'

const card_number = ref('')
const card_expiration = ref('')
const cvv = ref('')

const cardNumberValid = computed(() => {
  return card_number.value.length === 16 ? true : false
})

const cardExpirationValid = computed(() => {
  return card_expiration.value.length && card_expiration.value[2] === '/' ? true : false
})

const cvvValid = computed(() => {
  return cvv.value.length === 3 || cvv.value.length === 4 ? true : false
})

const isDisabled = computed(() => {
  return cardNumberValid && cardExpirationValid && cvvValid ? true : false
})

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
        name="email"
      />
      <BaseInput
        label="Full Name: "
        placeholder="Enter your full name"
        id="full-name"
        type="text"
        :class="$style.input"
        required
        name="full_name"
      />
      <BaseInput
        label="Card Number: "
        placeholder="Enter your Card Number"
        id="card-number"
        type="text"
        :class="$style.input"
        required
        name="card_number"
        v-model="card_number"
      />
      <BaseInput
        label="Expiration of Card: "
        placeholder="ex. 06/27"
        id="expiration-date"
        type="text"
        :class="$style.expiration"
        required
        name="expiration_date"
        v-model="card_expiration"
      />
      <BaseInput
        label="CVV: "
        placeholder="ex. 432"
        id="security-code"
        type="text"
        :class="$style.cvv"
        required
        name="cvv"
        v-model="cvv"
      />
    </form>
    <button
      :class="$style.button"
      form="checkout-form"
      :disabled="!isDisabled"
    >Submit</button>
    <p>{{ cardNumberValid }}</p>
    <p>{{ cardExpirationValid }}</p>
    <p>{{ cvvValid }}</p>
    <p>{{ isDisabled }}</p>
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

