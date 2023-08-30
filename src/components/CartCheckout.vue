<script setup>
import BaseInput from './BaseInput.vue'
import { ref, computed } from 'vue'

const card_number = ref('')
const card_expiration = ref('')
const cvv = ref('')

// validate card_number, card_expiration and cvv
const cardNumberValid = computed(() => {
  return card_number.value.length === 16 ? true : false
})

// cases are length is 5 and the 2nd index is a '/' character
const cardExpirationValid = computed(() => {
  return card_expiration.value.length === 5 && card_expiration.value[2] === '/' ? true : false
})

// cvv can be 3 or 4 in length
const cvvValid = computed(() => {
  return cvv.value.length === 3 || cvv.value.length === 4 ? true : false
})

// disable button with isDisabled based on validation of card_number, card_expiration and cvv
const isDisabled = computed(() => {
  return cardNumberValid && cardExpirationValid && cvvValid ? true : false
})

// only show error msg if the input is valid or the input value is not falsy(or empty)
const showErrorMsg = (inputValue, isInputValid, errorMsg) => {
  return isInputValid || !inputValue ? false : errorMsg
}

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
        :valid-error-msg="showErrorMsg(card_number, cardNumberValid, 'Card number should be 16 digits')"
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
        :valid-error-msg="showErrorMsg(card_expiration, cardExpirationValid, `Expiration Date should be in this format '09/25'`)"
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
        :valid-error-msg="showErrorMsg(cvv, cvvValid, 'CVV should be 3 or 4 digits')"
      />
    </form>
    <button
      :class="$style.button"
      form="checkout-form"
      :disabled="!isDisabled"
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

