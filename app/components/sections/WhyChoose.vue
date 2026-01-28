<template>
  <div class="relative z-30 bg-white w-full md:pb-10 lg:pt-30 pb-6 pt-0 px-3 lg:px-0 ">
    <section class="feature-section pb-20 bg-white max-w-6xl mx-auto">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 lg:grid-cols-2 md:gap-12 items-center">
          <!-- Left Column: Text Content -->
          <div class="content-wrapper">
            <div class="relative h-[500px] overflow-hidden">
              <Transition name="slide-right-to-left" mode="out-in">
                <div
                  :key="currentSlide"
                  class="absolute inset-0 flex flex-col justify-center"
                >
                  <div class="space-y-6 flex flex-col">
                    <span
                      class="text-emerald-500 font-bold text-lg tracking-[4px] uppercase mb-5"
                    >
                      Why Choose Us
                    </span>
                    <h2
                      class="text-3xl md:text-4xl font-bold text-gray-900 leading-tight"
                    >
                      {{ slides[currentSlide].title }}
                    </h2>
                    <p class="text-[#444444] text-base leading-relaxed">
                      We use as filler text for layouts, non-readability is of
                      great importance but because those who do not know how to
                      pursue pleasure rationally encounter consequences that are
                      extremely painful nor again is there anyone.
                    </p>
                    <ul class="space-y-3 grid grid-cols-2 gap-4 max-w-[350px]">
                      <li
                        v-for="(feature, idx) in slides[currentSlide].features"
                        :key="idx"
                        class="flex items-center gap-3 text-gray-700"
                      >
                        <svg
                          class="w-5 h-5 text-emerald-500 flex-shrink-0"
                          fill="currentColor"
                          viewBox="0 0 16 16"
                        >
                          <path
                            d="M12.736 3.97a.733.733 0 0 1 1.047 0c.286.289.29.756.01 1.05L7.88 12.01a.733.733 0 0 1-1.065.02L3.217 8.384a.757.757 0 0 1 0-1.06a.733.733 0 0 1 1.047 0l3.052 3.093l5.4-6.425z"
                          />
                        </svg>
                        <span class="text-sm whitespace-nowrap">{{
                          feature
                        }}</span>
                      </li>
                    </ul>
                  </div>
                </div>
              </Transition>
            </div>
          </div>

          <!-- Right Column: Image Slider -->
        <div class="slider-wrapper">
          <div class="relative h-[500px] flex gap-4">
            <!-- All Slides - Each stays in its natural position -->
            <div
              v-for="(slide, index) in slides"
              :key="index"
              class="slide-item transition-all duration-500 ease-out"
              :class="getSlideWidth(index)"
              @click="goToSlide(index)"
            >
              <div
                class="h-full rounded-2xl overflow-hidden relative cursor-pointer"
              >
                <!-- Overlay for inactive slides -->
                <div
                  v-if="index !== currentSlide"
                  class="absolute inset-0 z-10 bg-[linear-gradient(rgba(0,0,0,0.1)_0%,rgba(0,0,0,0.7)_100%)] opacity-80"
                ></div>

                <img
                  :src="slide.image"
                  :alt="slide.title"
                  class="w-full h-full object-cover"
                />

                <!-- Progress Bar - Only on active slide -->
                <div
                  v-if="index === currentSlide"
                  class="absolute bottom-8 left-6 right-6 z-20"
                >
                  <div
                    class="h-2 bg-white/20 rounded-full overflow-hidden backdrop-blur-sm"
                  >
                    <div
                      class="h-full bg-white rounded-full transition-all duration-300 ease-linear"
                      :style="{ width: `${progress}%` }"
                    ></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue";
import { useMotions } from "@vueuse/motion";

const { custom } = useMotions();

const slides = [
  {
    title: "Discover business Opportunities",
    features: [
      "Profile Consultation",
      "Asset management",
      "No-risk business idea",
    ],
    image: "https://staco-react.vercel.app/assets/feature-team1-CkrnjYrI.png",
  },
  {
    title: "Manage team increase productivity",
    features: ["99% Survey Report", "Trusted by teams", "Self-Service"],
    image: "https://staco-react.vercel.app/assets/feature-team2-BkN4ZF3A.png",
  },
  {
    title: "Strategic Business Growth",
    features: ["Market Analysis", "Revenue Optimization", "Risk Management"],
    image: "https://staco-react.vercel.app/assets/feature-team3-rNw9B1sS.png",
  },
];

const currentSlide = ref(0);
const progress = ref(0);
const autoplayInterval = ref(null);
const progressInterval = ref(null);
const SLIDE_DURATION = 5000; // 5 seconds per slide
const PROGRESS_UPDATE_INTERVAL = 50; // Update progress every 50ms

const visibleSlides = computed(() => {
  const total = slides.length;
  const prev = [];
  const next = [];

  // Get previous slide
  const prevIndex =
    currentSlide.value === 0 ? total - 1 : currentSlide.value - 1;
  prev.push(prevIndex);

  // Get next slide
  const nextIndex =
    currentSlide.value === total - 1 ? 0 : currentSlide.value + 1;
  next.push(nextIndex);

  return { prev, next };
});

const getSlideWidth = (index) => {
  if (index === currentSlide.value) {
    // Active slide - takes most space
    return "flex-grow opacity-100";
  } else {
    // Inactive slides - small width
    return "w-20 flex-shrink-0 opacity-60 hover:opacity-90";
  }
};

const goToSlide = (index) => {
  currentSlide.value = index;
  resetProgress();
};

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
  resetProgress();
};

const resetProgress = () => {
  progress.value = 0;
  clearInterval(progressInterval.value);
  startProgressBar();
};

const startProgressBar = () => {
  progressInterval.value = setInterval(() => {
    progress.value += 100 / (SLIDE_DURATION / PROGRESS_UPDATE_INTERVAL);
    if (progress.value >= 100) {
      progress.value = 100;
    }
  }, PROGRESS_UPDATE_INTERVAL);
};

const startAutoplay = () => {
  autoplayInterval.value = setInterval(() => {
    nextSlide();
  }, SLIDE_DURATION);
};

const stopAutoplay = () => {
  if (autoplayInterval.value) {
    clearInterval(autoplayInterval.value);
  }
  if (progressInterval.value) {
    clearInterval(progressInterval.value);
  }
};

onMounted(() => {
  startProgressBar();
  startAutoplay();
});

onUnmounted(() => {
  stopAutoplay();
});
</script>

<style scoped>
/* Right-to-Left Slide Transition for Text Content */
.slide-right-to-left-enter-active {
  transition: all 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.slide-right-to-left-leave-active {
  transition: all 0.7s cubic-bezier(0.55, 0.085, 0.68, 0.53);
}

.slide-right-to-left-enter-from {
  transform: translateX(100px);
  opacity: 0;
}

.slide-right-to-left-leave-to {
  transform: translateX(-120px);
  opacity: 0;
}

/* Fade Transition for Images */
.fade-enter-active {
  transition: opacity 0.7s ease;
}

.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Hover Effects */
.slide-item {
  transition: all 0.5s ease-out;
}

.slide-item:hover .h-full {
  transform: scale(1.02);
}

.slide-item .h-full {
  transition: transform 0.3s ease;
}

/* Container Responsive Padding */
.container {
  max-width: 1280px;
}

/* Custom Scrollbar for Overflow */
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: #10b981;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #059669;
}
</style>
