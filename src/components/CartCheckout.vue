<script setup>
import BaseInput from './BaseInput.vue'
</script>

<template>
  <section>
    <BaseInput
      label="Email: "
      placeholder="Enter your email"
      id="email"
      type="email"
    />
    <BaseInput
      label="Full Name: "
      placeholder="Enter your full name"
      id="full-name"
      type="text"
    />
    <BaseInput
      label="Card Number: "
      placeholder="Enter your Card Number"
      id="card-number"
      type="text"
    />
    <BaseInput
      label="Expiration of Card: "
      placeholder="ex. 06/27"
      id="expiration-date"
      type="text"
      class="expiration"
    />
    <BaseInput
      label="CVV: "
      placeholder="ex. 432"
      id="security-code"
      type="text"
      class="cvv"
    />
  </section>
</template>


<style scoped>
</style>

