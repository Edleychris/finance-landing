<script setup lang="ts">
defineProps<{ bg?: string }>()
</script>

<template>
  <section :class="[bg ?? 'w-full', '']">
    <slot />
  </section>
</template>
