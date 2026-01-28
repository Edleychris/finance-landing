<template>
  <nav class="fixed top-0 left-0 right-0 z-50 pt-6">
    <div class="max-w-6xl mx-auto">
      <div class="flex items-center justify-between w-full py-3">
        <div class="hidden md:flex items-center justify-center flex-1 w-full h-18.75">
          <div 
            ref="tabsContainer"
            class="relative h-full flex justify-center bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 backdrop-blur-sm rounded-full w-full px-2 py-2 shadow-2xl border border-gray-700/50"
            style="box-shadow: 0 10px 40px -5px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255, 255, 255, 0.1);"
          >
            <!-- Glossy Top Highlight -->
            <div class="absolute inset-x-0 top-0 h-px bg-gradient-to-r from-transparent via-white/20 to-transparent rounded-t-full" />
            
            <!-- Animated Background Indicator with Glassmorphism -->
            <div
              class="absolute top-4 left-2 rounded-full transition-all duration-500 ease-out"
              :style="{
                width: `${indicatorWidth}px`,
                height: 'calc(100% - 30px)',
                transform: `translateX(${indicatorLeft}px)`,
                background: 'linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(240, 240, 245, 0.9) 100%)',
                boxShadow: '0 4px 20px rgba(0, 0, 0, 0.15), inset 0 1px 0 rgba(255, 255, 255, 0.8), inset 0 -1px 0 rgba(0, 0, 0, 0.1)'
              }"
            >
              <!-- Inner glow effect -->
              <div class="absolute inset-0 rounded-full bg-gradient-to-b from-white/40 to-transparent" />
            </div>

            <!-- All Items Container -->
            <div class="relative flex gap-2 items-center justify-between w-full">
              <!-- Logo -->
              <NuxtLink 
                to="/"
                class="flex-shrink-0 z-10"
                @mouseenter="logoHovered = true"
                @mouseleave="logoHovered = false"
              >
                <div class="flex items-center space-x-2 px-3">
                  <icons name="staco-logo"/>
                </div>
              </NuxtLink>

              <!-- Navigation Items -->
              <div class="flex items-center space-x-1">
                <button
                  v-for="(item, index) in navItems"
                  :key="item.name"
                  :ref="el => { if (el) tabRefs[index] = el }"
                  @click="setActiveTab(index, item.href)"
                  @mouseenter="onTabHover(index)"
                  class="relative px-6 py-2.5 text-[15px] font-semibold rounded-full transition-all duration-300 whitespace-nowrap z-10 tracking-tight"
                  :class="[
                    activeTab === index 
                      ? 'text-gray-900' 
                      : 'text-gray-300 hover:text-white'
                  ]"
                  :style="activeTab === index ? 'text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1)' : ''"
                >
                  <span class="relative z-10">{{ item.name }}</span>
                  
                  <!-- Hover glow effect for inactive tabs -->
                  <div 
                    v-if="activeTab !== index && hoveredTab === index"
                    class="absolute inset-0 bg-white/5 rounded-full transition-opacity duration-300"
                  />
                </button>
              </div>

              <!-- CTA Buttons -->
              <div class="lg:flex hidden items-center space-x-3 flex-shrink-0 z-10 px-2">
                <button
                  class="px-5 py-2.5 text-sm font-semibold text-gray-300 hover:text-white transition-all duration-300 rounded-full hover:bg-white/10"
                >
                  Sign In
                </button>
                
                <button
                  class="group hidden lg:flex relative px-6 py-2.5 text-sm font-bold text-white rounded-full overflow-hidden transition-all duration-300 hover:scale-105 active:scale-95"
                  style="background: linear-gradient(135deg, #10B981 0%, #34D399 50%, #6EE7B7 100%); box-shadow: 0 4px 15px rgba(16, 185, 129, 0.4);"
                  @mouseenter="ctaHovered = true"
                  @mouseleave="ctaHovered = false"
                >
                  <!-- Animated gradient overlay -->
                  <div 
                    class="absolute inset-0 bg-gradient-to-r from-emerald-400 via-green-400 to-teal-400 transition-opacity duration-300"
                    :class="ctaHovered ? 'opacity-100' : 'opacity-0'"
                  />
                  
                  <!-- Shimmer effect -->
                  <div 
                    class="absolute inset-0 -translate-x-full transition-transform duration-1000 ease-out"
                    :class="ctaHovered ? 'translate-x-full' : '-translate-x-full'"
                    style="background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);"
                  />
                  
                  <span class="relative z-10 flex items-center gap-2">
                    Start Free
                    <Icon 
                      name="heroicons:arrow-right" 
                      class="w-4 h-4 transition-transform duration-300 group-hover:translate-x-1" 
                    />
                  </span>
                </button>
              </div>
            </div>
          </div>
        </div>


        <!-- Mobile Menu Button with Smooth Morphing -->
        <div class="md:hidden z-50 ml-4">
  <button
    @click="toggleMobileMenu"
    class="relative w-10 h-10 flex items-center justify-center
           text-gray-900 dark:text-white
           border-2 border-gray-300 dark:border-gray-600
           rounded-lg
           bg-white dark:bg-gray-900
           hover:bg-gray-100 dark:hover:bg-gray-800
           transition-all"
  >
    <div class="w-5 h-4 flex flex-col justify-between">
      <span
        class="block h-0.5 w-full rounded-full bg-gray-900 dark:bg-white
               transition-all duration-300 origin-center"
        :class="mobileMenuOpen ? 'rotate-45 translate-y-[7px]' : ''"
      />
      <span
        class="block h-0.5 w-full rounded-full bg-gray-900 dark:bg-white
               transition-all duration-300"
        :class="mobileMenuOpen ? 'opacity-0 scale-0' : ''"
      />
      <span
        class="block h-0.5 w-full rounded-full bg-gray-900 dark:bg-white
               transition-all duration-300 origin-center"
        :class="mobileMenuOpen ? '-rotate-45 -translate-y-[7px]' : ''"
      />
    </div>
  </button>
</div>

      </div>
    </div>

    <!-- Mobile Menu with Elegant Slide -->
     
    <MobileMenu 
      :open="mobileMenuOpen" 
      :items="navItems" 
      :active-index="activeTab"
      @close="mobileMenuOpen = false"
      @select="setActiveTab"
    />
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, nextTick } from 'vue';
import Icons from '../Icons/Icons.vue';
import MobileMenu from './MobileMenu.vue';

const mobileMenuOpen = ref(false)
const activeTab = ref(0)
const hoveredTab = ref<number | null>(null)
const logoHovered = ref(false)
const ctaHovered = ref(false)
const indicatorLeft = ref(0)
const indicatorWidth = ref(0)
const tabsContainer = ref<HTMLElement | null>(null)
const tabRefs = ref<(HTMLElement | null)[]>([])

const navItems = [
  { name: 'Home', href: '/' },
  { name: 'Services', href: '#services' },
  { name: 'About', href: '#about' },
  { name: 'Testimonials', href: '#testimonials' },
  { name: 'Contact', href: '#contact' }
]

const updateIndicator = (index: number) => {
  const tab = tabRefs.value[index]
  if (!tab || !tabsContainer.value) return

  const containerRect = tabsContainer.value.getBoundingClientRect()
  const tabRect = tab.getBoundingClientRect()
  
  indicatorLeft.value = tabRect.left - containerRect.left - 8
  indicatorWidth.value = tabRect.width
}

const setActiveTab = (index: number, href: string) => {
  activeTab.value = index
  updateIndicator(index)
  
  // Handle navigation
  if (href.startsWith('#')) {
    const element = document.querySelector(href)
    if (element) {
      const navHeight = 80
      const elementPosition = element.getBoundingClientRect().top + window.pageYOffset
      const offsetPosition = elementPosition - navHeight
      
      window.scrollTo({
        top: offsetPosition,
        behavior: 'smooth'
      })
    }
  } else {
    navigateTo(href)
  }
  
  mobileMenuOpen.value = false
}

const onTabHover = (index: number) => {
  hoveredTab.value = index
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

onMounted(async () => {
  await nextTick()
  updateIndicator(activeTab.value)
  
  let resizeTimeout: NodeJS.Timeout
  window.addEventListener('resize', () => {
    clearTimeout(resizeTimeout)
    resizeTimeout = setTimeout(() => {
      updateIndicator(activeTab.value)
    }, 150)
  })
})

// Update active tab based on scroll position
if (process.client) {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const id = entry.target.id
          const index = navItems.findIndex(item => item.href === `#${id}`)
          if (index !== -1 && index !== activeTab.value) {
            activeTab.value = index
            updateIndicator(index)
          }
        }
      })
    },
    { threshold: 0.5, rootMargin: '-100px 0px -50% 0px' }
  )

  onMounted(() => {
    navItems.forEach(item => {
      if (item.href.startsWith('#')) {
        const element = document.querySelector(item.href)
        if (element) observer.observe(element)
      }
    })
  })
}
</script>

<style scoped>
.transition-all,
.transition-transform,
.transition-opacity {
  will-change: transform, opacity;
}

nav {
  -webkit-backdrop-filter: blur(20px);
}

::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.2);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: rgba(0, 0, 0, 0.3);
}
</style>