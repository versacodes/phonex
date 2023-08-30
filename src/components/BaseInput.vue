<script>
// to use set automatic attribute inheritance in components
// Vue 3.3 can use defineOptions({})
export default {
  inheritAttrs: false,
}
</script>

<script setup>
</script>

<template>
  <label
    :for="$attrs.id"
    class="input_label"
  >{{$attrs.label}}</label>
  <input
    :id="$attrs.id"
    :placeholder="$attrs.placeholder"
    :type="$attrs.type"
    :class="$attrs.class"
  />
</template>

<style scoped>
.input_label {
  padding-bottom: 10px;
  margin-top: 10px;
}
.expiration, .cvv {
  width: 6rem;
} 
</style>
