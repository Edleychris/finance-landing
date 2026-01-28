<template>
  <Transition
    enter-active-class="transition duration-200 ease-out"
    enter-from-class="opacity-0 -translate-y-4"
    enter-to-class="opacity-100 translate-y-0"
    leave-active-class="transition duration-150 ease-in"
    leave-from-class="opacity-100 translate-y-0"
    leave-to-class="opacity-0 -translate-y-4"
  >
    <div
      v-if="open"
      class="md:hidden bg-white border-b border-gray-200 shadow-lg fixed top-0 h-screen"
    >
      <div class="px-4 py-6 space-y-2 mt-10">
        <button
          v-for="(item, index) in items"
          :key="item.name"
          @click="handleSelect(index, item.href)"
          class="w-full text-left px-4 py-3 text-base font-medium rounded-lg transition-all duration-200"
          :class="[
            activeIndex === index
              ? 'bg-blue-50 text-blue-600'
              : 'text-gray-700 hover:bg-gray-50 hover:text-gray-900'
          ]"
        >
          {{ item.name }}
        </button>
        
        <div class="pt-4 space-y-2">
          <UButton 
            size="lg" 
            block 
            variant="ghost"
            color="secondary"
          >
            Sign In
          </UButton>
          <UButton 
            size="lg" 
            block 
            color="primary"
          >
            Get Started
          </UButton>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup lang="ts">
interface Props {
  open: boolean
  items: Array<{ name: string; href: string }>
  activeIndex?: number
}

const props = defineProps<Props>()
const emit = defineEmits(['close', 'select'])

const handleSelect = (index: number, href: string) => {
  emit('select', index, href)
  emit('close')
}
</script>