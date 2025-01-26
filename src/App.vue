<template>
<div class="min-h-screen bg-gray-200 p-4">
  <h1 class="text-2xl font-bold mb-4 text-black">Drag & Drop Landing Builder</h1>

  <div class="flex gap-4">
    <div class="w-1/4 p-4 space-y-4 bg-gray-600 border rounded-md sticky h-fit top-0">
      <h2 class="font-semibold mb-2">Toolbox</h2>

      <div class="flex flex-col gap-4">
        <ToolboxItem blockType="text" @add:item="blocks.push({ type: 'text', content: '', id: 1 })">
          <span>📝 Text Block</span>
        </ToolboxItem>

        <ToolboxItem blockType="image" @add:item="blocks.push({ type: 'image', content: '', id: 1 })">
          <span>🖼 Image Block</span>
        </ToolboxItem>
      </div>
    </div>

    <div class="flex-1 p-4 border rounded-md bg-white">
      <h2 class="font-semibold mb-2 text-black">Editor Area</h2>
      <div class="space-y-4">
        <div v-for="block in blocks" class="p-4 border rounded-md shadow-sm bg-gray-50">
          <div class="flex justify-end gap-2 mb-2 text-sm">
            <button class="text-blue-600">Duplicate</button>
            <button class="text-red-600">Delete</button>
          </div>
          <TextBlock v-if="block.type === 'text'" v-model="block.content" />
          <ImageBlock v-else v-model="block.content"  />
        </div>
      </div>

      <button class="mt-4 bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600">
        Save
      </button>
    </div>
  </div>
</div>
</template>

<script lang="ts" setup>
import TextBlock from './components/TextBlock.vue';
import ImageBlock from './components/ImageBlock.vue';
import { ref } from 'vue';
import ToolboxItem from './components/ToolboxItem.vue';
import type { IBlock } from './types.ts';

const blocks = ref<IBlock[]>([
  { type: 'text', content: 'Hello World!', id: 1 },
  { type: 'image', content: '', id: 2 },
])
</script>
