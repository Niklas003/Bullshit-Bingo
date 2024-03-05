<template>
  <div class="flex">
    <input
      v-model="word"
      type="text"
      class="rounded-l p-2 bg-slate-300 font-semibold placeholder:text-slate-500"
      placeholder="Buzzzword eingeben"
    />
    <button
      type="button"
      class="bg-green-500 hover:bg-green-600 text-white p-2 rounded-r"
      @submit="handleInput"
      @click="handleInput"
    >
      Hinzufügen
    </button>
  </div>
</template>
<script setup lang="ts">
const word = ref("");
const emit = defineEmits(["inputWord"]);

function handleInput() {
  emit("inputWord", word.value);
  word.value = "";
}
</script>
