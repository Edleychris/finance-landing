<template>
  <div class="relative min-h-screen flex flex-col bg-transparent">
    <AppNavbar />
    <main class="flex-1 z-20 bg-inherit">
      <slot />
    </main>
    <AppFooter class="relative z-20 bg-[#ECf1f1]" />
    <div
      ref="disclaimerRef"
      class="sticky bottom-0 z-2 w-full transition-opacity duration-300"
      :class="{ 'opacity-0': !showDisclaimer }"
    >
      <AppDisclaimer />
    </div>

    <!-- Scroll Progress Button -->
    <Transition name="fade-slide">
      <button
        v-if="showScrollButton"
        @click="scrollToTop"
        class="fixed cursor-pointer bottom-20 right-8 z-50 w-14 h-14 rounded-full text-emerald-500 shadow-lg transition-all duration-300 flex items-center justify-center group"
        aria-label="Scroll to top"
      >
        <svg class="absolute inset-0 w-14 h-14 -rotate-90">
          <circle
            cx="28"
            cy="28"
            r="24"
            stroke="rgba(255, 255, 255, 0.2)"
            stroke-width="2"
            fill="none"
          />
          <circle
            cx="28"
            cy="28"
            r="24"
            stroke="rgb(13 172 129 / 80%)"
            stroke-width="2"
            fill="none"
            :stroke-dasharray="circumference"
            :stroke-dashoffset="progressOffset"
            class="transition-all duration-100"
            stroke-linecap="round"
          />
        </svg>
        <svg
          stroke="currentColor"
          fill="currentColor"
          stroke-width="0"
          viewBox="0 0 384 512"
          height="1em"
          width="1em"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M214.6 41.4c-12.5-12.5-32.8-12.5-45.3 0l-160 160c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0L160 141.2 160 448c0 17.7 14.3 32 32 32s32-14.3 32-32l0-306.7L329.4 246.6c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3l-160-160z"
          ></path>
        </svg>
      </button>
    </Transition>
  </div>
</template>

<script setup lang="ts">
import AppDisclaimer from "~/components/footer/AppDisclaimer.vue";
import AppFooter from "~/components/footer/AppFooter.vue";
import AppNavbar from "~/components/navbar/AppNavbar.vue";

const showScrollButton = ref(false);
const showDisclaimer = ref(true);
const scrollProgress = ref(0);
const disclaimerRef = ref<HTMLElement | null>(null);

defineProps<{
  bg?: string;
}>();
const circumference = 2 * Math.PI * 24;

const progressOffset = computed(() => {
  return circumference - (scrollProgress.value / 100) * circumference;
});
const currentColor = "rgb(13 172 129 / 80%)";
const handleScroll = () => {
  const scrollTop = window.scrollY;
  const docHeight = document.documentElement.scrollHeight - window.innerHeight;
  const scrollPercent = (scrollTop / docHeight) * 100;

  scrollProgress.value = Math.min(scrollPercent, 100);

  // Show button when scrolled down 200px
  showScrollButton.value = scrollTop > 200;

  const footer = document.querySelector("footer");
  if (footer) {
    const footerTop = footer.getBoundingClientRect().top + window.scrollY;
    const windowHeight = window.innerHeight;
    const currentScroll = scrollTop + windowHeight;

    showDisclaimer.value = currentScroll >= footerTop - 300;
  }
};

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
*,
::after,
::before,
body *,
html {
  font-family: "DM Sans", sans-serif;
  padding: 0;
  box-sizing: border-box;
}
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.3s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(20px) scale(0.9);
}
.fixed-bottom {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  z-index: 20;
  transition: opacity 0.3s ease;
}
.sticky {
  position: sticky;
  bottom: 0;
  z-index: 10;
}
</style>
