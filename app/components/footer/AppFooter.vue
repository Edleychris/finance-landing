<template>
  <footer class="relative  text-gray-300 bg-[#ECf1f1]">
    <!-- Main Footer Content -->
    <div class="max-w-337.5 mx-auto md:pt-30 pt-15 pb-10 bg-footer rounded-4xl flex flex-col justify-center">
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-12 mx-auto md:px-26 sm:px-20 px-8">
        <!-- Brand Section -->
        <div class="md:col-span-2 sm:col-span-1 col-span-2">
          <div class="flex items-center gap-3 mb-6">
            <Icons name="staco-logo" />
          </div>
          <p class="text-gray-400 sm:text-base text-sm font-semibold leading-relaxed mb-8">
            Staco is the dedicated platform for performance management that helps to grow your startup quickly
          </p>
          
          <!-- Social Icons -->
          <div class="flex gap-4">
<a 
  href="#" 
  class="social-link w-10 h-10 rounded-full border-2 border-gray-600 hover:border-gray-700 flex items-center justify-center transition-all hover:bg-gray-600"
  aria-label="Facebook"
>
  <span class="social-icon relative w-6 h-6 overflow-hidden">
    <Icons
      name="facebook-logo"
      class="icon transition-transform duration-300"
    />
  </span>
</a>

            <a 
              href="#" 
              class="w-10 h-10 rounded-full border border-gray-600 hover:border-emerald-500 flex items-center justify-center transition-all hover:bg-gray-700"
              aria-label="Twitter/X"
            >
              <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
              </svg>
            </a>
            <a 
              href="#" 
              class="w-10 h-10 rounded-full border border-gray-600 hover:border-emerald-500 flex items-center justify-center transition-all hover:bg-gray-700"
              aria-label="LinkedIn"
            >
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
              </svg>
            </a>
            <a 
              href="#" 
              class="w-10 h-10 rounded-full border border-gray-600 hover:border-emerald-500 flex items-center justify-center transition-all hover:bg-gray-700"
              aria-label="Instagram"
            >
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
              </svg>
            </a>
            <a 
              href="#" 
              class="w-10 h-10 rounded-full border border-gray-600 hover:border-emerald-500 flex items-center justify-center transition-all hover:bg-gray-700"
              aria-label="YouTube"
            >
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
              </svg>
            </a>
          </div>
        </div>

        <!-- Products Column -->
        <div class="mt-4">
          <h3 class="text-white md:text-lg sm:text-lg text-base font-bold mb-6 flex items-center gap-2">
            PRODUCTS <span>🔥</span>
          </h3>
          <ul class="space-y-4">
            <li>
              <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim  hover:text-white duration-300 transition-colors sm:text-base text-sm">
                HR Management
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim  hover:text-white duration-300 transition-colors sm:text-base text-sm">
                Invoice System
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim  hover:text-white duration-300 transition-colors sm:text-base text-sm">
                Email Marketing
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim  hover:text-white duration-300 transition-colors sm:text-base text-sm">
                Web Services
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim  hover:text-white duration-300 transition-colors sm:text-base text-sm">
                Digital Marketing
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Why Choose Column -->
        <div class="mt-4">
          <h3 class="text-white font-bold md:text-lg sm:text-lg text-base mb-6 flex items-center gap-2">
            WHY CHOOSE <span>☀️</span>
          </h3>
          <ul class="space-y-4">
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Customers
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Why Staco ?
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Book a demo
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Resources Column -->
        <div class="mt-4">
          <h3 class="text-white font-bold md:text-lg sm:text-lg text-base mb-6 flex items-center gap-2">
            RESOURCES <span>📘</span>
          </h3>
          <ul class="space-y-4">
            <li>
              <NuxtLink to="/blog" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Latest Blog
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Supports
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                Knowledgebase
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim">
                FAQs
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Company Column -->
        <div class="mt-4">
          <h3 class="text-white font-bold md:text-lg sm:text-lg text-base mb-6 flex items-center gap-2">
            COMPANY <span>💎</span>
          </h3>
          <ul class="space-y-4">
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim ">
                About
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim ">
                What we do
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim ">
                Contact us
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/" class="hover:text-white duration-300 transition-colors sm:text-base text-sm text-[#FFFFFFB2] font-meduim ">
                Careers
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="mt-16 pt-8 border-t border-gray-700 px-26">
        <div class="flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-base text-[#FFFFFFB2] font-meduim ">
            {{ currentYear }} Staco. All rights reserved.
          </p>
          <div class="flex gap-6">
            <NuxtLink to="/terms" class="text-[#FFFFFFB2] font-meduim text-base duration-300 transition-colors">
              Terms and conditions
            </NuxtLink>
            <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim text-base duration-300 transition-colors">
              Cookies
            </NuxtLink>
            <NuxtLink to="/" class="text-[#FFFFFFB2] font-meduim text-base duration-300 transition-colors">
              Privacy policy
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
// import Icons
const currentYear = new Date().getFullYear()
</script>

<style scoped>
footer {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}
.bg-footer{
    background: rgb(31, 35, 52);
}
/* Hover animation */
.social-link:hover .social-icon {
  transform: translateY(-18px);
}
.social-icon {
  position: relative;
  width: 24px;
  height: 24px;
  overflow: hidden !important; 
  display: flex;
  flex-direction: column;
  align-items: center;
}
.social-link .icon {
  width: 24px;
  height: 24px;
  display: block;
}

/* Hover animation */
.social-link:hover .icon:first-child {
  transform: translateY(-24px);
}

.social-link:hover .icon:last-child {
  transform: translateY(-24px);
}
.social-link:hover .icon:nth-child(1) {
  transform: translateY(-24px);
}

.social-link:hover .icon:nth-child(2) {
  transform: translateY(-24px);
}
</style>