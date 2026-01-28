<template>
  <div class="relative min-h-screen bg-white overflow-hidden">
    <Transition name="slide-down">
      <nav v-if="showNav" class="fixed top-0 left-0 right-0 z-50 bg-white border-b border-gray-100">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
          <div class="flex items-center justify-between h-20">
            <!-- Logo -->
            <div class="flex items-center gap-2">
              <div class="w-10 h-10 bg-gradient-to-br from-pink-400 to-green-400 rounded-lg"></div>
              <span class="text-2xl font-bold text-gray-900">Staco</span>
            </div>

            <!-- Navigation Links -->
            <div class="hidden lg:flex items-center gap-8">
              <UButton variant="ghost" color="gray" class="text-gray-700">
                Home
                <UIcon name="i-heroicons-chevron-down-20-solid" class="w-4 h-4 ml-1" />
              </UButton>
              <UButton variant="ghost" color="gray" class="text-gray-700">
                Pages
                <UIcon name="i-heroicons-chevron-down-20-solid" class="w-4 h-4 ml-1" />
              </UButton>
              <UButton variant="ghost" color="gray" class="text-gray-700">Services</UButton>
              <UButton variant="ghost" color="gray" class="text-gray-700">Blogs</UButton>
              <UButton variant="ghost" color="gray" class="text-gray-700">Contact Us</UButton>
            </div>

            <!-- Right Side Actions -->
            <div class="flex items-center gap-4">
              <UButton variant="ghost" color="gray" class="text-gray-700">
                <UIcon name="i-heroicons-globe-alt" class="w-5 h-5 mr-2" />
                EN
              </UButton>
              <UButton variant="ghost" color="gray" class="text-gray-700">Sign in</UButton>
              <UButton color="green" size="lg" class="bg-green-400 hover:bg-green-500 text-gray-900 font-medium">
                Start Free
              </UButton>
            </div>
          </div>
        </div>
      </nav>
    </Transition>

    <!-- Main Content -->
    <div class="max-w-7xl mx-auto px-6 lg:px-8" :class="showNav ? 'pt-32' : 'pt-16'">
      <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center min-h-[600px]">
        <!-- Left Content -->
        <div class="space-y-6">
          <div class="text-sm font-semibold tracking-wider text-green-500 uppercase">
            Why Choose Us
          </div>

          <!-- Animated Title -->
          <TransitionGroup name="fade-slide" mode="out-in">
            <h1 :key="currentSlide" class="text-5xl lg:text-6xl font-bold text-gray-900 leading-tight">
              {{ slides[currentSlide].title }}
            </h1>
          </TransitionGroup>

          <!-- Description -->
          <p class="text-gray-600 text-lg leading-relaxed max-w-xl">
            We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.
          </p>

          <!-- Benefits List with staggered animation -->
          <TransitionGroup name="list" tag="div" class="space-y-4">
            <div
              v-for="(benefit, index) in slides[currentSlide].benefits"
              :key="`${currentSlide}-${index}`"
              class="flex items-center gap-3"
              :style="{ transitionDelay: `${index * 100}ms` }"
            >
              <div class="flex-shrink-0 w-6 h-6 rounded-full bg-green-100 flex items-center justify-center">
                <UIcon name="i-heroicons-check" class="w-4 h-4 text-green-600" />
              </div>
              <span class="text-gray-900 font-medium">{{ benefit }}</span>
            </div>
          </TransitionGroup>
        </div>

        <!-- Right Images Grid with parallax effect -->
        <div class="relative h-[600px]">
          <TransitionGroup name="image-slide">
            <div
              v-for="(image, index) in slides[currentSlide].images"
              :key="`${currentSlide}-${index}`"
              class="absolute rounded-3xl overflow-hidden shadow-xl"
              :class="[
                index === 0 ? 'top-0 left-0 w-[45%] h-[65%] z-10' : '',
                index === 1 ? 'top-[15%] right-0 w-[48%] h-[70%] z-20' : '',
                index === 2 ? 'bottom-0 right-[15%] w-[40%] h-[45%] z-30' : '',
              ]"
              :style="{ transitionDelay: `${index * 150}ms` }"
            >
              <img
                :src="image.url"
                :alt="image.alt"
                class="w-full h-full object-cover"
              />
              <div
                v-if="image.overlay"
                class="absolute inset-0 bg-gradient-to-br from-yellow-400/20 to-transparent"
              ></div>
            </div>
          </TransitionGroup>

          <!-- Navigation Dots -->
          <div class="absolute -bottom-16 left-1/2 -translate-x-1/2 flex items-center gap-3">
            <button
              v-for="(slide, index) in slides"
              :key="index"
              @click="goToSlide(index)"
              class="group relative"
            >
              <div
                class="w-12 h-1 rounded-full transition-all duration-300"
                :class="
                  currentSlide === index
                    ? 'bg-green-500'
                    : 'bg-gray-300 group-hover:bg-gray-400'
                "
              ></div>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const showNav = ref(false)
const currentSlide = ref(0)
const autoplayInterval = ref<NodeJS.Timeout | null>(null)

interface Slide {
  title: string
  benefits: string[]
  images: {
    url: string
    alt: string
    overlay?: boolean
  }[]
}

const slides: Slide[] = [
  {
    title: 'Discover business Opportunities',
    benefits: ['Profile Consultation', 'Asset management', 'No-risk business idea'],
    images: [
      {
        url: 'https://images.unsplash.com/photo-1551836022-d5d88e9218df?w=800&h=1000&fit=crop',
        alt: 'Office workspace',
      },
      {
        url: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=800&h=1000&fit=crop',
        alt: 'Professional at work',
        overlay: true,
      },
      {
        url: 'https://images.unsplash.com/photo-1556761175-b413da4baf72?w=800&h=800&fit=crop',
        alt: 'Team collaboration',
      },
    ],
  },
  {
    title: 'Manage team increase productivity',
    benefits: ['99% Survey Report', 'Trusted by teams', 'Self-Service'],
    images: [
      {
        url: 'https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=800&h=1000&fit=crop',
        alt: 'Team meeting',
      },
      {
        url: 'https://images.unsplash.com/photo-1531482615713-2afd69097998?w=800&h=1000&fit=crop',
        alt: 'Productive workspace',
        overlay: true,
      },
      {
        url: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=800&h=800&fit=crop',
        alt: 'Team member',
      },
    ],
  },
  {
    title: 'Scale your business globally',
    benefits: ['Global Reach', 'Market Expansion', '24/7 Support'],
    images: [
      {
        url: 'https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?w=800&h=1000&fit=crop',
        alt: 'Modern office',
      },
      {
        url: 'https://images.unsplash.com/photo-1600880292203-757bb62b4baf?w=800&h=1000&fit=crop',
        alt: 'Business professional',
        overlay: true,
      },
      {
        url: 'https://images.unsplash.com/photo-1573497019940-1c28c88b4f3e?w=800&h=800&fit=crop',
        alt: 'Confident professional',
      },
    ],
  },
]

const goToSlide = (index: number) => {
  currentSlide.value = index
  resetAutoplay()
}

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length
}

const startAutoplay = () => {
  autoplayInterval.value = setInterval(() => {
    nextSlide()
  }, 5000)
}

const resetAutoplay = () => {
  if (autoplayInterval.value) {
    clearInterval(autoplayInterval.value)
  }
  startAutoplay()
}

onMounted(() => {
  setTimeout(() => {
    showNav.value = true
  }, 300)

  // Start autoplay
  startAutoplay()
})

onUnmounted(() => {
  if (autoplayInterval.value) {
    clearInterval(autoplayInterval.value)
  }
})
</script>

<style scoped>
.slide-down-enter-active {
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.slide-down-enter-from {
  transform: translateY(-100%);
  opacity: 0;
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-slide-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}

.fade-slide-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

.list-enter-active {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.list-leave-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: absolute;
}

.list-enter-from {
  opacity: 0;
  transform: translateX(-20px);
}

.list-leave-to {
  opacity: 0;
  transform: translateX(20px);
}

.image-slide-enter-active {
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.image-slide-leave-active {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: absolute;
}

.image-slide-enter-from {
  opacity: 0;
  transform: scale(0.9) translateY(20px);
}

.image-slide-leave-to {
  opacity: 0;
  transform: scale(1.05) translateY(-20px);
}

* {
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}
</style>