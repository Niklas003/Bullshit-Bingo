<template>
  <div>
    <titleHero />
    <div class="flex flex-col items-center my-4 space-y-8">
      <sizeInput @inputSize="(size:number) => gameSize = size" />
      <wordInput @inputWord="handleWord" />
      <ShuffleButton :disabled="words.length < 3" @click="shuffle(words)" />
    </div>
    <div class="mx-8">
      <div
        class="grid gap-2"
        :class="{ 'grid-cols-3': gameSize === 3, 'grid-cols-4': gameSize === 4, 'grid-cols-5': gameSize === 5 }"
      >
        <cell v-for="(i, index) in words" :word="i" @check-bingo="checkBingo(index)" />
        <emptyCell v-for="i in gameSize ** 2 - words.length" />
      </div>
    </div>
    <BingoHero v-if="showBingo" />
  </div>
</template>
<script setup lang="ts">
const words = ref<string[]>([]);
const gameSize = ref<number>(3);
const cellPosition = ref<boolean[][]>(Array(gameSize.value).fill(Array(gameSize.value).fill(false)));
const showBingo = ref(false);

function handleWord(word: string) {
  if (word !== "" && word.valueOf.length < gameSize.value ** 2) {
    words.value.push(word);
  }
}

function shuffle(array: string[]) {
  let currentIndex = array.length,
    randomIndex;

  // While there remain elements to shuffle.
  while (currentIndex > 0) {
    // Pick a remaining element.
    randomIndex = Math.floor(Math.random() * currentIndex);
    currentIndex--;

    // And swap it with the current element.
    [array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
  }

  return array;
}

function checkBingo(index: number) {
  //set the cell to the oppsite of the current value
  cellPosition.value[index % gameSize.value][Math.floor(index / gameSize.value)] =
    !cellPosition.value[index % gameSize.value][Math.floor(index / gameSize.value)];
  //check for a bingo
  if (checkRow(index) || checkColumn(index)) {
    showBingo.value = true;
  }
}

function checkRow(index: number) {
  return cellPosition.value[index % gameSize.value].every((i) => i);
}

function checkColumn(index: number) {
  return cellPosition.value.every((i) => i[index % gameSize.value]);
}
</script>
