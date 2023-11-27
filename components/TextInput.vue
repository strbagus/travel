<template>
  <div :class="$attrs.class">
    <label v-if="label" class="form-label" :for="id">{{ label }}:</label>
    <input :id="props.id" ref="input" v-bind="{ ...$attrs, class: null }" class="py-1 px-3 border"
      :class="[{ error: props.error }, props.inputClass]" :type="props.type" :value="props.modelValue"
      @input="$emit('update:modelValue', $event.target)" />
    <div v-if="error" class="form-error">{{ props.error }}</div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  id: {
    type: String,
    default() {
      return `text-input-${self.crypto.randomUUID()}`
    },
  },
  type: {
    type: String,
    default: 'text',
  },
  error: String,
  label: String,
  modelValue: {
    type: [String, Number],
  },
  inputClass: String,
})
const emit = defineEmits(['update:modelValue'])
const focus = (() => {
  // props.input.focus()
})
const select = (() => {
  // props.input.select()
})
const setSelectionRange = ((start, end) => {
  // props.input.setSelectionRange(start, end)
})
// inheritAttrs: false,
</script>
