<template>
        <div>
        <input v-model="size" type="number" class="rounded-l p-2 bg-slate-300 font-semibold placeholder:text-slate-500" placeholder="Größe festlegen">
        <button type="button" class="bg-green-500 hover:bg-green-600 text-white p-2 rounded-r" @submit="handleInput" @click="handleInput">Festlegen</button>
    </div>
</template>
<script setup lang="ts">
const size = ref<number>(3)
const emit = defineEmits(["inputSize"])

function handleInput() {
    emit("inputSize", size.value)
    size.value = 3
}
</script>