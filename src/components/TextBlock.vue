<template>
<textarea
  class="border border-gray-400 p-2 w-full text-black"
  rows="3"
  v-model="localValue"
></textarea>
</template>

<script setup lang="ts">
import { computed, defineProps, defineEmits } from 'vue'

const props = defineProps<{ modelValue: string }>()
const emits = defineEmits<{ (e: 'update:modelValue', val: string): void }>()

const localValue = computed({
  get: () => props.modelValue,
  set: val => emits('update:modelValue', val)
})
</script>
