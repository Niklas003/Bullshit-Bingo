<template>
  <div
    class="min-h-24 flex justify-center items-center font-bold text-2xl text-white rounded-sm cursor-pointer"
    :class="{ 'bg-slate-800': !isCheck, 'bg-green-500': isCheck }"
    @click="handleChecked"
  >
    {{ props.word }}
  </div>
</template>
<script setup lang="ts">
const isCheck = ref(false);
const props = defineProps<{
  word: string;
}>();
const emit = defineEmits(["checkBingo"]);

function handleChecked() {
  isCheck.value = !isCheck.value;
  emit("checkBingo");
}
</script>
