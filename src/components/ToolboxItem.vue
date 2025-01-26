<template>
<div
  class="border bg-white shadow-sm p-2 rounded-md flex items-center justify-center cursor-move text-black"
  @click="handleClick"
>
  <slot />
</div>
</template>

<script setup lang="ts">
import { defineEmits, defineProps } from 'vue';
import type { BlockType } from '../types'

const props = defineProps<{
  blockType: BlockType
}>()

const emits = defineEmits<{ (e: 'add:item', val: string): void }>()

function handleClick() {
  emits('add:item', props.blockType)
}
</script>
