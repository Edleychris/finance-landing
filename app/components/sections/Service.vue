<template>
  <UContainer class="relative z-30 bg-white w-full md:pb-10 md:pt-34 pb-6 pt-20">
    <div ref="sectionRef" class="max-w-7xl mx-auto md:px-4 px-2 lg:px-16">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(card, index) in cards"
          :key="index"
          class="bg-[#ECF1F1] group rounded-[30px] p-8 transition duration-300"
          :class="sectionVisible ? 'animate-card' : 'hidden-card'"
          :style="{ transitionDelay: `${index * 300}ms` }"
        >
          <div class="mb-8">
            <Icons :name="card.icon" />
          </div>

          <h2 class="text-xl font-semibold mb-3 text-black">
            {{ card.title }}
          </h2>

          <p class="text-[#444444] text-base font-medium mb-18 leading-7.5">
            {{ card.description }}
          </p>
          <a href="#" class="flex items-center justify-between gap-3">
            <span
              class="font-bold text-[#444444] transition duration-300 group-hover:text-[rgb(68,196,134)]"
            >
              Learn more
            </span>

            <div
              class="w-10 h-10 rounded-full bg-black/10 flex items-center justify-center transition duration-300 group-hover:bg-[rgb(68,196,134)]"
            >
              <svg
                width="17"
                height="14"
                viewBox="0 0 17 14"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="transition duration-300 stroke-black group-hover:stroke-white group-hover:-rotate-[35deg]"
              >
                <path
                  d="M9.19336 1L15.1934 7L9.19336 13"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M1 7H14.0545"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
          </a>
        </div>
      </div>
    </div>
  </UContainer>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Icons from "../Icons/Icons.vue";

const sectionVisible = ref(false);
const sectionRef = ref(null);

const cards = [
  {
    title: "Used advanced technologies",
    description:
      "I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born",
    icon: "adh-tech",
  },
  {
    title: "Clean design & Typography",
    description:
      "I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born",
    icon: "clean-typo",
  },
  {
    title: "Best customer support",
    description:
      "I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born",
    icon: "cs-support",
  },
];
onMounted(() => {
  if (!process.client) return;

  if (!("IntersectionObserver" in window)) {
    sectionVisible.value = true;
    return;
  }

  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        sectionVisible.value = true;
        observer.disconnect();
      }
    },
    { threshold: 0.2 },
  );

  if (sectionRef.value) {
    observer.observe(sectionRef.value);
  }
});
</script>

<style scoped>
.bg-wh {
  background: white !important;
}
.hidden-section {
  opacity: 0;
  transform: translateY(100px);
}
.animate-section {
  opacity: 1;
  transform: translateY(0);
  transition: all 1s ease;
}

.hidden-card {
  opacity: 0;
  transform: translateX(-100px);
}
.animate-card {
  opacity: 1;
  transform: translateX(0);
  transition: all 0.8s ease;
}
/* Fix typo */
@media (prefers-reduced-motion: reduce) {
  .hidden-section,
  .hidden-card,
  .animate-section,
  .animate-card {
    transition: none;
  }
}
</style>
