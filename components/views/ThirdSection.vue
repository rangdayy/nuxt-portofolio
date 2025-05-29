<template>
  <div class="max-w-4xl mx-auto py-10 px-5 grid grid-cols-3 gap-5">
    <div class="col-span-3 md:col-span-1">
      <Motion
        as="div"
        :initial="{ opacity: 0, x: -40, filter: 'blur(5px)' }"
        :while-in-view="{
          opacity: 1,
          x: 0,
          filter: 'blur(0px)',
        }"
        :transition="{
          delay: 0.5,
          duration: 0.8,
          ease: 'easeInOut',
        }"
        class="relative rounded-2xl p-1"
      >
        <GlowingEffect :spread="30" :glow="true" :disabled="false" :proximity="60" :inactive-zone="0.4" />
        <Lens :hovering="hovering" @hover-update="setHovering">
          <img
            src="https://instagram.fupg7-1.fna.fbcdn.net/v/t39.30808-6/469218679_18473247193042778_9045402448796363051_n.jpg?stp=dst-jpg_e35_tt6&efg=eyJ2ZW5jb2RlX3RhZyI6IkZFRUQuaW1hZ2VfdXJsZ2VuLjE0NDB4MTgwMC5zZHIuZjMwODA4LmRlZmF1bHRfaW1hZ2UifQ&_nc_ht=instagram.fupg7-1.fna.fbcdn.net&_nc_cat=102&_nc_oc=Q6cZ2QFHz2Xp7fH4B2y1aG8SX2gHWiiqJhaW-IblhNqxVu9Liv0ifvMxqUaIkBNEFQHEdco&_nc_ohc=XSdPkDqROPYQ7kNvwEFI52t&_nc_gid=zLLmFmKWl2iifKrxzzNJkQ&edm=AP4sbd4AAAAA&ccb=7-5&ig_cache_key=MzQxNjMyMjI0MjMzNzQ1MTQ4OQ%3D%3D.3-ccb7-5&oh=00_AfK_9VDkqc6FKYoqP1Mo9ZiAb1GhMSFpbQ3oYRZh5sl_Nw&oe=683C91E2&_nc_sid=7a9f4b"
            alt=""
          />
        </Lens>
      </Motion>
    </div>
    <div class="col-span-3 md:col-span-2">
       <Motion
        as="div"
        :initial="{ opacity: 0, x: 40, filter: 'blur(5px)' }"
        :while-in-view="{
          opacity: 1,
          x: 0,
          filter: 'blur(0px)',
        }"
        :transition="{
          delay: 0.5,
          duration: 0.8,
          ease: 'easeInOut',
        }"
        class=" space-y-5"
      >
      <div class="space-y-2">
        <p class="text-4xl font-thin">I’m a web dev who mess around</p>
        <FlipWords :words="['Design', 'Code', 'and occasionally', 'a camera']" :duration="2000" class="text-3xl md:text-6xl font-bold !text-lime-500 min-h-11" />
      </div>
      <p class="font-thin italic tracking-widest">Still learning, still curious, always caffeinated.</p>
      <div>
        <Marquee pause-on-hover class="[--duration:20s]">
          <template v-for="skill in firstHalf" :key="skill.name">
            <div class="flex flex-row items-center gap-2 px-4 py-1 rounded-lg bg-zinc-100 dark:bg-zinc-800 border border-zinc-100 dark:border-zinc-700 text-zinc-800 dark:text-zinc-100">
              <Icon :name="skill.icon" class="w-8 h-8" />
              <span class="text-sm font-medium">{{ skill.name }}</span>
            </div>
          </template>
        </Marquee>
        <Marquee reverse pause-on-hover class="[--duration:20s]">
          <template v-for="skill in secondHalf" :key="skill.name">
            <div class="flex flex-row items-center gap-2 px-4 py-1 rounded-lg bg-zinc-100 dark:bg-zinc-800 border border-zinc-100 dark:border-zinc-700 text-zinc-800 dark:text-zinc-100">
              <Icon :name="skill.icon" class="w-8 h-8" />
              <span class="text-sm font-medium">{{ skill.name }}</span>
            </div>
          </template>
        </Marquee>
      </div>
      </Motion>
    </div>
  </div>
</template>

<script setup lang="ts">
import FlipWords from "../inspira/FlipWords.vue";
import GlowingEffect from "../inspira/GlowingEffect.vue";
import Lens from "../inspira/Lens.vue";
import Marquee from "../inspira/Marquee.vue";

const hovering = ref(false);

const setHovering = (value: boolean) => {
  hovering.value = value;
};

const skills = [
  {
    name: "JavaScript",
    icon: "logos:javascript",
  },
  {
    name: "TypeScript",
    icon: "logos:typescript-icon",
  },
  {
    name: "React",
    icon: "logos:react",
  },
  {
    name: "Vue",
    icon: "logos:vue",
  },
  {
    name: "Nuxt",
    icon: "logos:nuxt-icon",
  },
  {
    name: "CSS",
    icon: "logos:css-3",
  },
  {
    name: "Bootstrap",
    icon: "logos:bootstrap",
  },
  {
    name: "TailwindCSS",
    icon: "logos:tailwindcss-icon",
  },
  {
    name: "Figma",
    icon: "logos:figma",
  },
  {
    name: "Github",
    icon: "logos:github-icon",
  },
  {
    name: "Gitlab",
    icon: "logos:gitlab",
  },
];

const firstHalf = computed(() => {
  return skills.slice(0, skills.length / 2);
});

const secondHalf = computed(() => {
  return skills.slice(skills.length / 2, skills.length);
});
</script>
