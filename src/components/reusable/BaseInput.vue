<template>
  <label :for="uuid">{{ label }}</label>
  <input
    class="field"
    v-bind="$attrs"
    :placeholder="label"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    :id="uuid"
    :aria-describedby="error ? `${uuid}-error` : null"
    :aria-invalid="error ? true : null"
  />
  <p v-if="error" class="error" :id="`${uuid}-error`" aria-live="assertive">
    {{ error }}
  </p>
</template>

<script>
import UniqueID from '@/features/UniqueID'
export default {
  props: {
    label: {
      type: String,
      default: '',
    },
    modelValue: {
      type: [String, Number],
      default: '',
    },
    error: {
      type: String,
      default: '',
    },
  },
  setup() {
    const uuid = UniqueID().getID()
    return {
      uuid,
    }
  },
}
</script>

<style></style>
