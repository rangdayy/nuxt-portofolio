<template>
  <div class="overflow-x-hidden dark:bg-zinc-900 bg-white text-zinc-900 dark:text-zinc-100 tracking-wide">
    <!-- <ClientOnly>
      <button @click="colorMode.preference= 'light'">{{ colorMode.value }}</button>
      <button @click="colorMode.preference= 'dark'">{{ colorMode.value }}</button>
    </ClientOnly> -->
    <NuxtPage></NuxtPage>
  </div>
</template>

<script setup lang="ts">
// const colorMode = useColorMode();
</script>
