<template>
  <div class="max-w-4xl mx-auto px-5 w-full py-10">
    <div class="space-y-4 py-10">
      <Motion
        as="h1"
        :initial="{ opacity: 0, y: 40, filter: 'blur(5px)' }"
        :while-in-view="{
          opacity: 1,
          y: 0,
          filter: 'blur(0px)',
        }"
        :transition="{
          delay: 0.5,
          duration: 0.8,
          ease: 'easeInOut',
        }"
        class="text-4xl font-thin"
      >
        Places I’ve Been
      </Motion>
      <Motion
        as="h1"
        :initial="{ opacity: 0, y: 40, filter: 'blur(5px)' }"
        :while-in-view="{
          opacity: 1,
          y: 0,
          filter: 'blur(0px)',
        }"
        :transition="{
          delay: 0.5,
          duration: 0.8,
          ease: 'easeInOut',
        }"
        class="text-4xl font-thin"
      >
        <GenerateText class="text-xl font-thin" words="A few cities that shaped my journey — from student life to career adventures and everything in between."></GenerateText>
      </Motion>
    </div>
    <Motion
      as="div"
      :initial="{ opacity: 0, y: 40, filter: 'blur(5px)' }"
      :while-in-view="{
        opacity: 1,
        y: 0,
        filter: 'blur(0px)',
      }"
      :transition="{
        delay: 0.5,
        duration: 0.8,
        ease: 'easeInOut',
      }"
    >
      <div class="bg-zinc-50 dark:bg-zinc-900">
        <WorldMap :dots="dots" :map-color="isDark ? '#FFFFFF40' : '#00000040'" :map-bg-color="isDark ? 'rgb(24 24 27)' : 'white'" :line-color="'rgb(132 204 22 )'" />
      </div>
    </Motion>
  </div>
</template>

<script lang="ts" setup>
import GenerateText from "../inspira/GenerateText.vue";
import WorldMap from "../inspira/WorldMap.vue";

const dots = [
  {
    start: {
      lat: 15,
      lng: 26,
    },
    end: {
      lat: 0,
      lng: 26,
    },
  },
  {
    start: {
      lat: 0,
      lng: 26,
    },
    end: {
      lat: -22,
      lng: -35,
    },
  },
  {
    start: {
      lat: -22,
      lng: -35,
    },
    end: {
      lat: -20,
      lng: -43,
    },
  },
  {
    start: {
      lat: -20,
      lng: -43,
    },
    end: {
      lat: -14,
      lng: -48,
    },
  },
  {
    start: {
      lat: -14,
      lng: -48,
    },
    end: {
      lat: -18,
      lng: -53,
    },
  },
  {
    start: {
      lat: 0,
      lng: 26,
    },
    end: {
      lat: 30,
      lng: 34,
    },
  },
  {
    start: {
      lat: 0,
      lng: 26,
    },
    end: {
      lat: -15,
      lng: -85,
    },
  },
  {
    start: {
      lat: 0,
      lng: 26,
    },
    end: {
      lat: 34,
      lng: 50,
    },
  },
  {
    start: {
      lat: 0,
      lng: 26,
    },
    end: {
      lat: -24,
      lng: -24,
    },
  },
];

const isDark = computed(() => useColorMode().value == "dark");
</script>
