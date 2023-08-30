<script setup>
defineOptions({
  inheritAttrs: false,
})
defineProps({
  modelValue: String,
  validErrorMsg: String,
})
defineEmits(['update:modelValue'])
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
    :name="$attrs.name"
    required="required"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
  <span class="error-msg" v-if="validErrorMsg">{{ validErrorMsg }}</span>
</template>

<style scoped>
.input_label {
  padding-bottom: 10px;
  margin-top: 10px;
  font-size: 1.1rem;
  color: #333;
}

.input_label ~ .input_label {
  margin-top: 1.4rem;
}

.expiration, .cvv {
  width: 6rem;
}

input {
  padding: 0.8rem;
  color: #333;
  outline-color: #97f;
}

.error-msg {
  color: #f45;
  margin-top: 5px;
  font-size: 0.8rem;
  display: block;
}
</style>
