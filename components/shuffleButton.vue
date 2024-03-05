<template>
  <div>
    <button
      type="button"
      :disabled="props.disabled"
      class="bg-green-500 hover:bg-green-600 disabled:bg-green-500/50 text-white p-4 rounded font-bold text-xl"
    >
      Mischen
    </button>
  </div>
</template>
<script setup lang="ts">
const props = defineProps<{
  disabled: boolean;
}>();
</script>
