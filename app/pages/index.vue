<script setup lang="ts">
import Benefit from '~/components/review/Benefit.vue';
import Financial from '~/components/review/Financial.vue';
import Service from '~/components/sections/Service.vue';
import WhyChoose from '~/components/sections/WhyChoose.vue';
defineProps<{
  bg?: string
}>()
</script>

<template>
 <section class="p-0 w-full">
  <SectionWrapper>
    <HeroView />
  </SectionWrapper>
  <SectionWrapper bg="bg-[#FFFFFF]">
    <Service />
  </SectionWrapper>

  <SectionWrapper bg="bg-[#FFFFFF]">
    <Financial />
  </SectionWrapper>
  <SectionWrapper bg="bg-[#FFFFFF]">
    <WhyChoose />
  </SectionWrapper>

  <!-- <SectionWrapper bg="bg-[#FFFFFF]">
    <Benefit />
  </SectionWrapper> -->

  <SectionWrapper bg="bg-[#ECF1F1]">
    <Review />
  </SectionWrapper>
</section>

</template>

