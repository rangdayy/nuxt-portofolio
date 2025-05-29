<template>
  <div class="max-w-4xl mx-auto px-5">
    <Timeline :items="data" class="bg-zinc-50 dark:bg-zinc-900">
      <template v-for="item in data" :key="item.id + 'template'" #[`${item.id}title`]>
        <Motion
          :initial="{ opacity: 0, y: 40, filter: 'blur(5px)' }"
          :while-in-view="{
            opacity: 1,
            y: 0,
            x: 0,
            filter: 'blur(0px)',
          }"
          :transition="{
            duration: 0.5,
            ease: 'easeInOut',
          }"
        >
          <h1 class="mb-3 text-4xl">{{ item.label }}</h1>
          <p class="text-xl font-thin dark:text-zinc-100">
            {{ item.range }}
          </p>
        </Motion>
      </template>
      <template v-for="item in data" :key="item.id + 'template'" #[item.id]>
        <Motion
          :initial="{ opacity: 0, x: 40, filter: 'blur(5px)' }"
          :while-in-view="{
            opacity: 1,
            y: 0,
            x: 0,
            filter: 'blur(0px)',
          }"
          :transition="{
            duration: 0.5,
            ease: 'easeInOut',
          }"
        >
          <div>
            <h3 class="mb-3 block text-left text-xl md:text-2xl font-bold text-neutral-500 dark:text-neutral-500">
              {{ item.institution }}
            </h3>
          </div>
          <p class="font-thin text-neutral-800 md:text-sm dark:text-neutral-200">{{ item.content }}</p>
        </Motion>
      </template>
    </Timeline>
  </div>
</template>

<script setup lang="ts">
import Timeline from "../inspira/Timeline.vue";
const data = [
  {
    id: "1",
    label: "College",
    range: "2017 – Oct 2021",
    institution: "Universitas Kristen Satya Wacana",
    content: "Studied Informatics Engineering and explored my passion for coding, design, and frontend development.",
  },
  {
    id: "2",
    label: "Internship",
    range: "Sep 2020 – Sep 2021",
    institution: "PT Sumber Alfaria Trijaya Tbk (Alfamart)",
    content: "Interned as a Python Developer, working on a Promotion Application System for a year before graduation.",
  },
  {
    id: "3",
    label: "Frontend Developer",
    range: "May 2022 – Jan 2024",
    institution: "PT Aistech Global Solution",
    content: "Worked as a Vue-based frontend developer, building modern web applications and sharpening UI/UX skills.",
  },
  {
    id: "4",
    label: "Senior Software Engineer",
    range: "Jan 2024 – Jan 2025",
    institution: "PT Eguard Teknologi Indonesia",
    content: "Served as a Senior Frontend Developer, focusing on scalable frontend architecture and performance.",
  },
  {
    id: "5",
    label: "Frontend Web Developer (Remote)",
    range: "Jan 2025 – Present",
    institution: "PT Anugerah Untung Bersama",
    content: "Currently working remotely on frontend projects, delivering responsive and polished user experiences.",
  },
  {
    id: "6",
    label: "IT & System Management",
    range: "Jun 2025 – Present",
    institution: "Dinas Pemuda dan Olahraga Makassar",
    content: "Also working in the public sector managing IT systems and supporting digital initiatives.",
  },
];
</script>
