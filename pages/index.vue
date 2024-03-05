<template>
    <div>
        <div class="flex justify-center items-center my-4 space-x-1">
            <sizeInput @inputSize="handleSize" />
            <wordInput @inputWord="handleWord" />
        </div>
        <div class="mx-8">
            <div class='grid grid-cols-4 gap-2'>
            <cell  v-for="i in words" :word="i" />
        </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

const words = ref<string[]>([])
const gameSize = ref<number>(3)

function handleSize(size: number) {
    if(size > 0 && size < 10){
        gameSize.value = size
    }   
}

function handleWord(word: string) {
    if (word !== '' && word.valueOf.length < 16){
        words.value.push(word)
    }
}
</script>