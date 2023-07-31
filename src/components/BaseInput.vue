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
  >Input</label>
  <input
    :id="$attrs.id"
    :placeholder="$attrs.placeholder"
    :type="$attrs.type"
  />
</template>

<style scoped>
.input_label {
  padding-bottom: 10px;
}
</style>
