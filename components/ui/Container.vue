<!-- components/ui/Container.vue -->
<template>
<div
  :class="[
    'mx-auto px-4 sm:px-6 lg:px-8',
    containerSizes[size],
    className
  ]"
>
    <slot />
  </div>
</template>

<script setup>

const props = defineProps({
  className: { type: String, default: '' },
  size:      { type: String, default: 'lg' }
})

const containerSizes = {
  sm:   'max-w-2xl',
  md:   'max-w-4xl',
  lg:   'max-w-6xl',
  xl:   'max-w-7xl',
  full: 'max-w-full'
}
</script>