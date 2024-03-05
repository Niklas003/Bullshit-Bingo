<template>
  <div class="flex space-x-2 mx-4">
    <div
      @click="handleInput(3)"
      class="flex flex-col items-center bg-slate-300 rounded-md p-4 cursor-pointer font-bold text-xl text-slate-800 hover:bg-slate-400"
    >
      <span>9</span>
      <span class="font-semibold">,,drei Gewinnt''</span>
    </div>
    <div
      @click="handleInput(4)"
      class="flex flex-col items-center bg-slate-300 rounded-md p-4 cursor-pointer font-bold text-xl text-slate-800 hover:bg-slate-400"
    >
      <span>16</span>
      <span class="font-semibold">,,vier Gewinnt''</span>
    </div>
    <div
      @click="handleInput(5)"
      class="flex flex-col items-center bg-slate-300 rounded-md p-4 cursor-pointer font-bold text-xl text-slate-800 hover:bg-slate-400"
    >
      <span>25</span>
      <span class="font-semibold">,,fünf Gewinnt''</span>
    </div>
  </div>
</template>
<script setup lang="ts">
const emit = defineEmits(["inputSize"]);

function handleInput(size: number) {
  emit("inputSize", size);
}
</script>
