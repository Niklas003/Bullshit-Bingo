<template>
  <div>
    <NuxtPage />
  </div>
</template>
<script setup lang="ts">
useHead({
  title: "Bullsh💩t Bingo - Game für Uni, Arbeit, Schule",
  meta: [{ name: "description", content: "Bullshit Bingo für die Uni, Schule oder Arbeit" }],
  bodyAttrs: {
    class: "test",
  },
  script: [{ innerHTML: "console.log('Hello world')" }],
});
</script>
