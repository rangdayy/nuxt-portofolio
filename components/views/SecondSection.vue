<template>
  <div class="min-h-screen max-w-3xl mx-auto py-10 px-5 space-y-3 md:font-normal font-thin ">
    <Motion
      as="p"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)', x: -20 }"
      :while-in-view="{
        opacity: 1,
        y: 0,
        x: 0,
        filter: 'blur(0px)',
      }"
      :transition="{
        delay: 0.5,
        duration: 0.5,
        ease: 'easeInOut',
      }"
      class="text-base md:text-xl"
    >
      Hi there 👋
    </Motion>
    <Motion
      as="p"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)', x: -20 }"
      :while-in-view="{
        opacity: 1,
        y: 0,
        x: 0,
        filter: 'blur(0px)',
      }"
      :transition="{
        delay: 0.5,
        duration: 0.5,
        ease: 'easeInOut',
      }"
      class="text-base md:text-xl"
    >
      this is my little spot on the internet
    </Motion>
    <Motion
      as="p"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)', x: 20 }"
      :while-in-view="{
        opacity: 1.5,
        y: 0,
        x: 0,
        filter: 'blur(0px)',
      }"
      :transition="{
        delay: 1,
        duration: 0.5,
        ease: 'easeInOut',
      }"
      class="text-base md:text-xl text-right pt-10"
    >
      cool, let me check it real quick 🏃
    </Motion>
    <Motion
      as="p"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)', x: -20 }"
      :while-in-view="{
        opacity: 1,
        y: 0,
        x: 0,
        filter: 'blur(0px)',
      }"
      :transition="{
        delay: 2,
        duration: 0.5,
        ease: 'easeInOut',
      }"
      class="text-base md:text-xl pt-10 pb-3"
    >
      for starter just click the button below 👇
    </Motion>
    <Motion
      :initial="{ opacity: 0, filter: 'blur(5px)', y: 20, x: -20 }"
      :transition="{
        delay: 2.5,
        duration: 0.5,
        ease: 'easeInOut',
      }"
      :while-in-view="{
        opacity: 1,
        filter: 'blur(0px)',
        y: 0,
        x: 0,
      }"
      class="flex flex-wrap gap-2"
    >
      <ShimmerButton background="rgb(24 24 27)" shimmer-size="2px" @click="$emit('scrollToAboutMe')">
        <span class="text-zinc-900 dark:text-white"> about me</span>
      </ShimmerButton>
      <ShimmerButton background="rgb(24 24 27)" shimmer-size="2px" @click="$emit('scrollToTimeline')">
        <span class="text-zinc-900 dark:text-white"> timeline</span>
      </ShimmerButton>
      <ShimmerButton background="rgb(24 24 27)" shimmer-size="2px" @click="$emit('scrollToMap')">
        <span class="text-zinc-900 dark:text-white"> places i've been</span>
      </ShimmerButton>
    </Motion>
  </div>
</template>

<script setup lang="ts">
import ShimmerButton from "../inspira/ShimmerButton.vue";
defineEmits(["scrollToAboutMe", "scrollToTimeline", "scrollToMap"]);
</script>
