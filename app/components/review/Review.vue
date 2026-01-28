<template>
  <div bg="bg-[#ECF1F1]" class="min-h-screen bg-[#ECf1f1] flex items-center px-6 lg:px-0 justify-center py-20">
    <div ref="sectionRef" 
          :class="sectionVisible ? 'animate-section' : 'hidden-section'"
     class="bg-white rounded-4xl max-w-6xl pt-15  customers-quote-card relative">
      <div  class="grid md:grid-cols-2 gap-8 p-12 ">
        <!-- Left side - Image -->
        <div class="relative ">

          <div class="customers-quote-bg absolute left-20">
            <img src="data:image/svg+xml,%3csvg%20width='320'%20height='298'%20viewBox='0%200%20320%20298'%20fill='none'%20xmlns='http://www.w3.org/2000/svg'%3e%3cpath%20d='M20%20150C20%2067.1573%2087.1573%200%20170%200V0C252.843%200%20320%2067.1573%20320%20150V298H20V150Z'%20fill='%23004D42'/%3e%3cpath%20d='M0%20150C0%2067.1573%2067.1573%200%20150%200V0C232.843%200%20300%2067.1573%20300%20150V298H0V150Z'%20fill='%23B2EDA1'/%3e%3c/svg%3e" alt="quote background">
        </div>
            <div class="customers-quote-img">
            <span class="quote-customers-img bottom-2">
                <img :src="currentContent.image" 
                :alt="currentContent.name"
                class="w-full h-full object-cover transition-opacity duration-500">
            </span>
        </div>
        </div>

        <!-- Right side - Content -->
        <div class="flex flex-col space-y-6">
          <div class="quote-icon mb-10">
            <img src="data:image/svg+xml,%3csvg%20width='70'%20height='70'%20viewBox='0%200%2070%2070'%20fill='none'%20xmlns='http://www.w3.org/2000/svg'%3e%3cpath%20d='M-2.6963e-07%2035C-1.20718e-07%2015.67%2015.67%201.20718e-07%2035%202.6963e-07C54.33%204.18543e-07%2070%2015.67%2070%2035L70%2070L35%2070C15.67%2070%20-4.18543e-07%2054.33%20-2.6963e-07%2035Z'%20fill='%2344C486'/%3e%3ccircle%20cx='34.7168'%20cy='34.7163'%20r='25'%20fill='white'/%3e%3cpath%20d='M31.2857%2027C32.3071%2027%2033.1429%2027.8%2033.1429%2028.7778C33.1429%2029.7556%2032.3071%2030.5556%2031.2857%2030.5556C29.6329%2030.5556%2028.1286%2031.2489%2027.1257%2032.3511C30.19%2032.1022%2032.8829%2034.2889%2033.1243%2037.2222C33.3657%2040.1556%2031.1%2042.7333%2028.0171%2042.9822C24.9529%2043.2311%2022.2786%2041.0444%2022.0186%2038.0933C22%2037.9511%2022%2037.8089%2022%2037.6667V35.8889C22%2030.9822%2026.16%2027%2031.2857%2027ZM46.1429%2027C47.1643%2027%2048%2027.8%2048%2028.7778C48%2029.7556%2047.1643%2030.5556%2046.1429%2030.5556C44.49%2030.5556%2043.0043%2031.2489%2041.9829%2032.3511C45.0471%2032.1022%2047.74%2034.2889%2047.9814%2037.2222C48.2414%2040.1556%2045.9571%2042.7333%2042.8929%2042.9644C39.81%2043.2311%2037.1357%2041.0444%2036.8757%2038.0933C36.8571%2037.9511%2036.8571%2037.8089%2036.8571%2037.6667V35.8889C36.8571%2030.9822%2041.0171%2027%2046.1429%2027ZM27.5714%2035.8889C26.55%2035.8889%2025.7143%2036.6889%2025.7143%2037.6667C25.7143%2038.6444%2026.55%2039.4444%2027.5714%2039.4444C28.5929%2039.4444%2029.4286%2038.6444%2029.4286%2037.6667C29.4286%2036.6889%2028.5929%2035.8889%2027.5714%2035.8889ZM42.4286%2035.8889C41.4071%2035.8889%2040.5714%2036.6889%2040.5714%2037.6667C40.5714%2038.6444%2041.4071%2039.4444%2042.4286%2039.4444C43.45%2039.4444%2044.2857%2038.6444%2044.2857%2037.6667C44.2857%2036.6889%2043.45%2035.8889%2042.4286%2035.8889Z'%20fill='%23242549'/%3e%3c/svg%3e" alt="quote icon">
        </div>
        <div class="flex flex-col justify-center space-y-6 flex-1">
          <p 
            class="text-gray-700 text-lg leading-relaxed transition-opacity duration-500"
            :class="{ 'opacity-0': isTransitioning, 'opacity-100': !isTransitioning }"
          >
            {{ currentContent.testimonial }}
          </p>

          <div 
            class="transition-opacity duration-500"
            :class="{ 'opacity-0': isTransitioning, 'opacity-100': !isTransitioning }"
          >
            <h3 class="text-2xl font-bold text-gray-900">{{ currentContent.name }}</h3>
            <p class="text-gray-900 font-medium">{{ currentContent.role }}</p>
          </div>
        </div>
        </div>
      </div>

      <!-- Partner logos -->
      <div class="border-t-2 border-gray-200 px-16 py-6 relative">
        <div class="absolute left-0 -top-px w-full h-[2.5px] overflow-hidden">
          <div 
            class="absolute h-full w-20 bg-gradient-to-r from-emerald-600 to-teal-700 animate-slide-horizontal"
          ></div>
        </div>
        
        <div class="flex items-center justify-between opacity-40 grayscale">
            <span>
                <img style="display: block;-webkit-user-select: none;margin: auto;background-color: transparent;transition: background-color 300ms;" src="data:image/png;base64,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">
            </span>
            <span>
                <img style="display: block;-webkit-user-select: none;margin: auto;background-color: transparent;transition: background-color 300ms;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFIAAAAWCAYAAABT5cvhAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAASJSURBVHgB5Vm7cts4FAVASKFTqVSJGdkZlSpdsvLSW+kTUm65n7Glyy1TpnSVKEmjMqVKTizNsFTJyuFEJJBz+RIJUQkVyR4nPoUpQSCAe3Hu05xZUMpzpTybGGMU53zImBlsf+URxiOMrdPUWYThuzU7MbD/oP49DOfRnnkuHm5tKMbcmB23t73m3v1t8OZC15dSGs9ebB+SJP6vfvjzc98zRg+EMOHd3acFOxBKTQdSxv82DsjT27a1RqPrKedmsh0x0XL54YYdgYuLv0EgPa2PQcabLsoU5QdSApTos45KhBDruhJJMDw8zgUO40zPz68v2TOCpD+FOXmHvKi1aZh1kx3ZDFLk5/Ib3bbWidrOd9bL5fvP7A9Bpshez50as/ujECwwRgSbja6oLSUfkv8k87WmEzsrNnPOGv4KilfE1vI71qD3/xxFEhuhRGWNx1Kyt0EwC1veobEWBfA51OOX74Ohc/aMAEaejaEAa5jPg+B9yA4AmSkuJej1XqrN5j44NoL+bpCOY5Q9mCRfD464RcQDuzXM37189epq/eXLxyBPKdwhXMGg7j5g+sPR6KqIkDxerT7M2AlAFob9G/4akXdRj7xKXY2lFMPaaeL9/rqnRqO/hnBL4zIVhByhEOmink3IXMBtFkSTfoVN8HkeHlUOmKaMNgkgFKUzbosPdus+E2hVpNZc4ZLafhm0+XUs2xI43RB/KkU6jkNKqe2dxYBWRUrpFJe93QwkUMhMFDKdwXI5m2fzoMSBdcBGzgRmjaGUMWtFJyZ1Sqf2IU+n9IQ9TXhK+SDeLKSobQnKrWgrQGv2I0FOYpJPGZQzwzKi3UqP2J2x/41kDwyqDPINXR8XUjGbXEiaxrfsiSNJxP9lKUz+XogXr4XglX8lX0/PFkWao0zRRunkUfnEdnbQpfQihdvuhoCEXtnseBjcVxZKsQNl9AJxxa9NcLMAR42I5oFE43AU8ZDSZIJorcd1Vj0G7OhYIq+12aP7zn4/jeDudsYl7B8dnW20JaoShcvIXbAmE4SiFB6Pqsinhm/fBBUrOxB2zQy4vV7vWSvrVyDSlAf2IHIk3+4L/s7o9/UJ/T4f2iNktZJyoIsLP7TqbTR33X9QeQQI7wHRmQ6DfJJSodMcx3Ihp4PAeroxQikcHjXCHBJQXzbm7laCJosfmbVvNmwOu39trZBVHlqzCfkEcrDHKVHHVh8Zl/UCl+WTa3FXq9kbdhLcRy01gId9FMuaKRlhOitSSk1nDClzoLQHhGswsuhi5Y1dYiUec/aAaHMhUOyAsoBCuJOAGI71wp2dsEeRcRxs5vm7VGHtmnWaiiwQV3GcakZMvs3ToW7AbXTuJz7GZZUgC/v5rC5y/nTOvJCrmZDf3b0j7S7ybjY1b/WwqMXpFsk0YyhvjVIppA5R07+ZBXV/ym8tjd/ssrA2DqcnhYm4xT/Uiswhwvr9Rs6YJJuddfL1eah1uhUZHffyMwkH/3vjOGdeIcOwVAzOiFYfD+L4a+Q4fa/+Li5g7Ti62n+1+nhLumieN3MPmN/Mb78DG0gyTcEe7X4AAAAASUVORK5CYII=">
            </span>
            <span>
                <img style="display: block;-webkit-user-select: none;margin: auto;background-color: transparent;transition: background-color 300ms;" src="data:image/png;base64,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">
            </span>
            <span>
                <img style="display: block;-webkit-user-select: none;margin: auto;background-color: transparent;transition: background-color 300ms;" src="data:image/png;base64,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">
            </span>
            <span>
                <img style="display: block;-webkit-user-select: none;margin: auto;background-color: transparent;transition: background-color 300ms;" src="data:image/png;base64,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">
            </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const testimonials = [
  {
    name: 'Dennis Lail',
    role: 'Marketer',
    testimonial: 'Making this the first true 😍 generator on the Internet. It uses a dictionary of over words, combined with a handful of model sentence structures, to generate 👏👏',
    image: 'https://staco-react.vercel.app/assets/quote-img3-CPzHyTHF.png'
  },
  {
    name: 'Peter Leo,',
    role: 'CTO - Criston',
    testimonial: 'Very denounce with righteous indignation and dislike men who are so beguiled and demoralized by the charms of pleasure of the moment, combined with a handfulso blinded by desire encounter 🥰 🤜 🤛',
    image: 'https://staco-react.vercel.app/assets/quote-img4-DCywOInX.png'
  },
  {
    name: 'Dennis Lail',
    role: 'Marketer',
    testimonial: 'Making this the first true 😍 generator on the Internet. It uses a dictionary of over words, combined with a handful of model sentence structures, to generate 👏👏',
    image: 'https://staco-react.vercel.app/assets/quote-img5-DdgwyiXw.png'
  },
  {
    name: 'Roe Smith',
    role: 'Director, Growth Marketing',
    testimonial: 'I must explain to you how all this mistaken. Tdea of denouncing pleasure and praising pain was born and I will give you a complete account. 😍',
    image: 'https://staco-react.vercel.app/assets/bohemian-man-CVN_j-Wi.png'
  },
  {
    name: 'Aurthoe De,',
    role: 'CEO - Dorid Co',
    testimonial: 'We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pleasure rationally encounter consequences that are pleasure rationally encounter ❤️ ❤️',
    image: 'https://staco-react.vercel.app/assets/quote-img2-Bs5ctuYK.png'
  },
]

const currentIndex = ref(0)
const isTransitioning = ref(false)
let intervalId = null
const sectionVisible = ref(false);
const sectionRef = ref(null);

const currentContent = computed(() => testimonials[currentIndex.value])

const rotateContent = () => {
  isTransitioning.value = true
  
  setTimeout(() => {
    currentIndex.value = (currentIndex.value + 1) % testimonials.length
    isTransitioning.value = false
  }, 500)
}

onMounted(() => {
  intervalId = setInterval(rotateContent, 5000)

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
  if (intervalId) {
    clearInterval(intervalId)
  }
})
</script>

<style scoped>
@keyframes slide-horizontal {
  0% {
    left: -20%;
  }
  100% {
    left: 100%;
  }
}

.animate-slide-horizontal {
  animation: slide-horizontal 10s linear infinite;
}
.customers-quote-img {
    position: relative;
    min-height: 298px;
    max-width: 220px;
    width: 100%;
    margin: auto;
    display: flex;
    align-items: flex-end;
    justify-content: center;
}
.customers-quote-img .quote-customers-img {
    position: relative;
    z-index: 2;
}

.customers-quote-card::before {
    content: url(data:image/png;base64,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);
    position: absolute;
    left: 0px;
    top: 48px;
    z-index: 0;
}
.customers-quote-card > * {
  position: relative;
  z-index: 1;
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

</style>