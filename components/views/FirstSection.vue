<template>
  <div class="relative min-h-screen dark:bg-zinc-900 flex items-center py-10">
    <ParticlesBackground class="absolute inset-0" :quantity="100" :ease="100" :color="isDark ? '#FFF' : '#000'" :staticity="10" refresh> </ParticlesBackground>
    <Motion
      as="div"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)' }"
      :while-in-view="{
        opacity: 1,
        y: 0,
        filter: 'blur(0px)',
      }"
      :while-hover="{
        y: -10,
        scale: 1.2,
      }"
      :transition="{
        delay: 0.3,
        duration: 0.8,
        ease: 'easeInOut',
      }"
      class="relative flex flex-col items-center justify-center gap-4 px-4 max-w-2xl mx-auto dark:text-white text-center"
    >
      <ClientOnly>
        <h1 class="text-5xl mb-2 font-bold">
          Hello,
          <TextHighlight class="bg-gradient-to-r from-[#cae54e] via-[#84cc16] to-[#16a34a]"> its me cho! </TextHighlight>
        </h1>
        <p class="text-xl md:text-2xl leading-loose">
          <GenerateText class="font-thin" words="i’m into coding, design, and all things frontend. Just building cool stuff one pixel at a time." />
        </p>
      </ClientOnly>
    </Motion>
  </div>
</template>

<script setup lang="ts">
import GenerateText from "../inspira/GenerateText.vue";
import ParticlesBackground from "../inspira/ParticlesBackground.vue";
import TextHighlight from "../inspira/TextHighlight.vue";

const isDark = useColorMode().value === "dark";
</script>
