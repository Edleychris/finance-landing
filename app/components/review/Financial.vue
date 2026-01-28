<template>
  <div class="max-h-302.5 sm:py-30 py-15 bg-white w-full -px-6 flex items-center justify-center relative">
    <div ref="sectionRef" class="max-w-7xl w-full mx-auto px-6 lg:px-16">
      <div 
          :class="sectionVisible ? 'animate-section' : 'hidden-section'"
        ref="heroSection" 
        class="bg-[#004D42] w-full rounded-[30px] px-8 sm:px-12 lg:px-[70px] overflow-hidden relative"
      >
        <div class="grid grid-cols-1 md:grid-cols-2 md:gap-8 lg:gap-0 items-center">
          <div class="md:py-12 pt-12 lg:py-16">
            <h2 class="md:text-4xl lg:text-5xl sm:text-5xl text-3xl top-19 absolute font-extrabold text-white leading-tight md:mb-8">
              We are building<br />
              financial foundations
            </h2>
            
            <UButton
              to="/#contact-us"
              color="primary"
              size="xl"
              class="bg-[#B2EDA1] md:mt-35 sn:mt-56 mt-35 hover:bg-[#A0DC8F] text-[#111111] font-bold rounded-full px-8 h-[60px] inline-flex items-center justify-center gap-2 transition-all duration-300 hover:gap-3"
            >
              Let's Talk
              <svg 
                width="17" 
                height="14" 
                viewBox="0 0 17 14" 
                fill="none" 
                xmlns="http://www.w3.org/2000/svg"
                class="transition-transform duration-300 group-hover:translate-x-1"
              >
                <path 
                  d="M9.19336 1L15.1934 7L9.19336 13" 
                  stroke="currentColor" 
                  stroke-width="2" 
                  stroke-miterlimit="10" 
                  stroke-linecap="round" 
                  stroke-linejoin="round"
                />
                <path 
                  d="M1 7H14.0545" 
                  stroke="currentColor" 
                  stroke-width="2" 
                  stroke-miterlimit="10" 
                  stroke-linecap="round" 
                  stroke-linejoin="round"
                />
              </svg>
            </UButton>
          </div>

          <!-- Right Column - Animated Image -->
          <div class="flex items-end justify-end h-[300px] md:h-[350px] lg:h-[400px] relative overflow-hidden">
            <div 
              class="transition-transform duration-300 ease-out absolute bottom-0 right-0 w-full max-w-[420px]"
              :style="arrowsStyle"
            >
              <img
                src="data:image/svg+xml,%3csvg%20width='372'%20height='250'%20viewBox='0%200%20372%20250'%20fill='none'%20xmlns='http://www.w3.org/2000/svg'%3e%3cpath%20d='M120.81%20137.65L15.7733%20235.304L0%20249.943L46.5404%20250L58.3819%20235.35L137.134%20137.65H120.81Z'%20fill='%2395A196'/%3e%3cpath%20d='M149.295%20137.65L90.2023%20235.304L81.3184%20249.943L127.882%20250L132.822%20235.35L165.618%20137.65H149.295Z'%20fill='%2385A088'/%3e%3cpath%20d='M177.781%20137.65L164.622%20235.304L162.627%20249.943L209.225%20250L207.276%20235.35L194.105%20137.65H177.781Z'%20fill='%235C9F63'/%3e%3cpath%20d='M206.268%20137.65L239.052%20235.304L243.947%20249.943L290.579%20250L281.73%20235.35L222.591%20137.65H206.268Z'%20fill='%23439F4D'/%3e%3cpath%20d='M234.754%20137.65L313.471%20235.304L325.267%20249.943L371.922%20250L356.172%20235.35L251.077%20137.65H234.754Z'%20fill='%23019D12'/%3e%3cpath%20d='M137.134%20105.312H120.811V137.65H137.134V105.312Z'%20fill='%2322675D'/%3e%3cpath%20d='M165.62%2086.6959H149.297V137.65H165.62V86.6959Z'%20fill='%2330766C'/%3e%3cpath%20d='M194.105%2066.1309H177.781V137.65H194.105V66.1309Z'%20fill='%233A8A7F'/%3e%3cpath%20d='M222.591%2045.1879H206.268V137.65H222.591V45.1879Z'%20fill='%236CA88B'/%3e%3cpath%20d='M251.077%2023.8549H234.754V137.65H251.077V23.8549Z'%20fill='%2344C486'/%3e%3cpath%20d='M120.81%20137.65L15.7733%20235.304L0%20249.943L46.5404%20250L58.3819%20235.35L137.134%20137.65H120.81Z'%20fill='white'/%3e%3cpath%20d='M149.295%20137.65L90.2023%20235.304L81.3184%20249.943L127.882%20250L132.822%20235.35L165.618%20137.65H149.295Z'%20fill='white'/%3e%3cpath%20d='M177.781%20137.65L164.622%20235.304L162.627%20249.943L209.225%20250L207.276%20235.35L194.105%20137.65H177.781Z'%20fill='white'/%3e%3cpath%20d='M206.268%20137.65L239.052%20235.304L243.947%20249.943L290.579%20250L281.73%20235.35L222.591%20137.65H206.268Z'%20fill='white'/%3e%3cpath%20d='M234.754%20137.65L313.471%20235.304L325.267%20249.943L371.922%20250L356.172%20235.35L251.077%20137.65H234.754Z'%20fill='white'/%3e%3cpath%20d='M127.919%2087.8536L108.764%20114.609H147.085L127.919%2087.8536Z'%20fill='%2322675D'/%3e%3cpath%20d='M157.596%2065.168L138.43%2091.9115H176.751L157.596%2065.168Z'%20fill='%2330766C'/%3e%3cpath%20d='M185.52%2043.0557L166.365%2069.7992H204.687L185.52%2043.0557Z'%20fill='%233A8A7F'/%3e%3cpath%20d='M214.419%2022.1124L195.264%2048.856H233.585L214.419%2022.1124Z'%20fill='%236CA88B'/%3e%3cpath%20d='M242.536%200L223.381%2026.7435H261.702L242.536%200Z'%20fill='%2344C486'/%3e%3c/svg%3e"
                alt="Financial Growth"
                class="w-full h-auto"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, computed } from 'vue'

const heroSection = ref<HTMLElement | null>(null)
const lastScrollY = ref(0)
const currentTranslateY = ref(0)
const isScrolling = ref(false)
const sectionVisible = ref(false);
const sectionRef = ref(null);

const arrowsStyle = computed(() => {
  return {
    transform: `translateY(${currentTranslateY.value}px)`,
    transition: isScrolling.value ? 'transform 0.3s ease-out' : 'transform 0.5s ease-out'
  }
})

const handleScroll = () => {
  if (!heroSection.value) return
  
  isScrolling.value = true
  
  const rect = heroSection.value.getBoundingClientRect()
  const scrollY = window.scrollY
  
  // Calculate how much the hero section is visible
  const heroTop = rect.top
  const heroHeight = rect.height
  const windowHeight = window.innerHeight
  
  // Calculate visibility ratio (0 to 1)
  const visibilityRatio = 1 - Math.min(1, Math.max(0, heroTop / windowHeight))
  
  // Calculate movement based on scroll direction and hero visibility
  const scrollDelta = scrollY - lastScrollY.value
  lastScrollY.value = scrollY
  
  // Only move when hero section is in viewport
  if (heroTop < windowHeight && heroTop + heroHeight > 0) {
    // REVERSED: Move image UP when scrolling DOWN, DOWN when scrolling UP
    const movement = -scrollDelta * 0.3 * visibilityRatio // Note the negative sign here
    currentTranslateY.value += movement
    
    // Clamp the movement between -50px and 150px for smooth animation
    currentTranslateY.value = Math.max(-0, Math.min(150, currentTranslateY.value))
  }
  
  // Reset isScrolling after a short delay for smoother transitions
  clearTimeout((window as any).scrollTimeout)
  ;(window as any).scrollTimeout = setTimeout(() => {
    isScrolling.value = false
  }, 100)
}

onMounted(() => {
  lastScrollY.value = window.scrollY
  window.addEventListener('scroll', handleScroll, { passive: true })

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
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  if ((window as any).scrollTimeout) {
    clearTimeout((window as any).scrollTimeout)
  }
})
</script>
<style scoped>

.hidden-section {
  opacity: 0;
  transform: translateY(100px);
}
.animate-section {
  opacity: 1;
  transform: translateY(0);
  transition: all 1s ease;
}

</style>