<template>
  <section class="">
    <FirstSection></FirstSection>
    <SecondSection @scrollToAboutMe="scrollToAboutMe" @scrollToTimeline="scrollToTimeline" @scrollToMap="scrollToMap"></SecondSection>
    <div ref="aboutme">
      <ThirdSection></ThirdSection>
    </div>
    <div ref="timeline">
      <FourthSection></FourthSection>
    </div>
    <div ref="map">
      <FifthSection></FifthSection>
    </div>
  </section>
</template>

<script setup lang="ts">
import FifthSection from "~/components/views/FifthSection.vue";
import FirstSection from "~/components/views/FirstSection.vue";
import FourthSection from "~/components/views/FourthSection.vue";
import SecondSection from "~/components/views/SecondSection.vue";
import ThirdSection from "~/components/views/ThirdSection.vue";

const aboutme = ref(null);
const timeline = ref(null);
const map = ref(null);

const scrollToAboutMe = () => {
  if (aboutme.value) {
    const content = aboutme.value as any;
    window.scrollTo({
      top: content?.offsetTop,
      behavior: "smooth",
    });
  }
};

const scrollToTimeline = () => {
  if (timeline.value) {
    const content = timeline.value as any;
    window.scrollTo({
      top: content?.offsetTop,
      behavior: "smooth",
    });
  }
};

const scrollToMap = () => {
  if (map.value) {
    const content = map.value as any;
    window.scrollTo({
      top: content?.offsetTop,
      behavior: "smooth",
    });
  }
};
</script>
