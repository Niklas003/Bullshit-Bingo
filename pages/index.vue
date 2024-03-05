<template>
  <div>
    <div class="flex flex-col items-center my-4 space-y-8">
      <sizeInput @inputSize="(size:number) => gameSize = size" />
      <wordInput @inputWord="handleWord" />
    </div>
    <div class="mx-8">
      <div
        class="grid gap-2"
        :class="{ 'grid-cols-3': gameSize === 3, 'grid-cols-4': gameSize === 4, 'grid-cols-5': gameSize === 5 }"
      >
        <cell v-for="i in words" :word="i" />
        <emptyCell v-for="i in gameSize ** 2 - words.length" />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";

const words = ref<string[]>([]);
const gameSize = ref<number>(3);

function handleWord(word: string) {
  if (word !== "" && word.valueOf.length < gameSize.value ** 2) {
    words.value.push(word);
  }
}
</script>
