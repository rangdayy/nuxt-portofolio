<template>
  <div>
    <div ref="timelineContainerRef" class="relative w-full md:px-10">
      <div ref="timelineRef" class="relative z-0 mx-auto max-w-7xl pb-20">
        <div v-for="(item, index) in props.items" :key="item.id + index" class="flex justify-start pt-10 md:gap-10 md:pt-40">
          <div class="sticky top-40 z-40 flex max-w-xs flex-col items-center self-start lg:max-w-sm md:w-full md:flex-row">
            <div class="absolute left-3 flex size-10 items-center justify-center rounded-full bg-white md:left-3 dark:bg-black">
              <div class="size-4 rounded-full border border-neutral-300 bg-neutral-200 p-2 dark:border-neutral-700 dark:bg-neutral-800" />
            </div>
            <div class="hidden text-xl font-bold text-neutral-500 md:block md:pl-20 md:text-5xl dark:text-neutral-500">
              <slot :name="`${item.id}title`">
                <h3>
                  {{ item.label }}
                </h3>
              </slot>
            </div>
          </div>
          <div class="relative w-full pl-20 pr-4 md:pl-4">
            <slot :name="item.id"></slot>
          </div>
        </div>
        <div
          :style="{
            height: height + 'px',
          }"
          class="absolute left-8 top-0 w-[2px] overflow-hidden bg-[linear-gradient(to_bottom,var(--tw-gradient-stops))] from-transparent from-0% via-neutral-200 to-transparent to-[99%] [mask-image:linear-gradient(to_bottom,transparent_0%,black_10%,black_90%,transparent_100%)] md:left-8 dark:via-neutral-700"
        >
          <Motion
            as="div"
            :style="{
              height: heightTransform,
              opacity: opacityTransform,
            }"
            class="absolute inset-x-0 top-0 w-[2px] rounded-full bg-gradient-to-t from-[#cae54e] from-0% via-[#84cc16] to-lime-500"
          >
          </Motion>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { useScroll, useTransform } from "motion-v";
import type { HTMLAttributes } from "vue";

interface Props {
  containerClass?: HTMLAttributes["class"];
  class?: HTMLAttributes["class"];
  items?: {
    id: string;
    label: string;
  }[];
}

const props = withDefaults(defineProps<Props>(), {
  items: () => [],
});

const timelineContainerRef = ref<HTMLElement | null>(null);
const timelineRef = ref<HTMLElement | null>(null);
const height = ref(0);

onMounted(async () => {
  await nextTick();
  if (timelineRef.value) {
    const rect = timelineRef.value.getBoundingClientRect();
    height.value = rect.height;
  }
});

const { scrollYProgress } = useScroll({
  target: timelineRef,
  offset: ["start 10%", "end 50%"],
});

const opacityTransform = useTransform(scrollYProgress, [0, 0.1], [0, 1]);
const heightTransform = ref(useTransform(scrollYProgress, [0, 1], [0, 0]));

watch(height, (newHeight) => {
  heightTransform.value = useTransform(scrollYProgress, [0, 1], [0, newHeight]);
});
</script>
