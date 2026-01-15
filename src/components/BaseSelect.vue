<script setup>
const props = defineProps({
    label: {
        type: String,
        default: '',
    },
    modelValue: {
        type: [String, Number],
        default: '',
    },
    options: {
        type: Array,
        required: true,
    }
})
</script>
<template>
    <label v-if="label">{{ label }}</label>
      <select 
        v-bind="
            { 
                ...$attrs,
                onChange: ($event) => { $emit('update:modelValue', $event.target.value) }
             }
        "
        :value="modelValue"
        class="field"
      >
        <option
          v-for="option in options"
          :value="option"
          :key="option"
          :selected="option === modelValue"
        >{{ option }}</option>
      </select>
</template>