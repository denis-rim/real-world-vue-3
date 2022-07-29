<template>
  <label :for="uuid" v-if="label">{{ label }}</label>
  <select
    :id="uuid"
    :value="modelValue"
    class="field"
    v-bind="{
      ...$attrs,
      onChange: ($event) => {
        $emit('update:modelValue', $event.target.value)
      },
    }"
  >
    <option
      v-for="option in options"
      :value="option"
      :key="option"
      :selected="option === modelValue"
    >
      {{ option }}
    </option>
  </select>
</template>

<script>
import UniqueID from '@/features/UniqueID'
export default {
  props: {
    label: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default: () => [],
    },
    modelValue: {
      type: [String, Number],
      required: true,
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
