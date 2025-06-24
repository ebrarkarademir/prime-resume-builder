<!-- components/ui/Button.vue -->
<template>
  <button
  :class="[
    'inline-flex items-center justify-center font-medium rounded-lg transition-fast focus:outline-none focus:ring-2 focus:ring-offset-2 disabled:opacity-50 disabled:cursor-not-allowed touch-manipulation select-none',
    buttonVariants[variant],
    buttonSizes[size],
    className
  ]"
    :disabled="disabled || isLoading"
    :aria-disabled="disabled || isLoading"
    v-bind="attrs"
  >
    <svg
      v-if="isLoading"
      class="animate-spin -ml-1 mr-2 h-4 w-4"
      fill="none"
      viewBox="0 0 24 24"
    >
      <circle
        class="opacity-25"
        cx="12"
        cy="12"
        r="10"
        stroke="currentColor"
        stroke-width="4"
      />
      <path
        class="opacity-75"
        fill="currentColor"
        d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
      />
    </svg>
    <slot />
  </button>
</template>

<script setup>
import { useAttrs } from 'vue'

const props = defineProps({
  variant:   { type: String,  default: 'primary' },
  size:      { type: String,  default: 'md' },
  isLoading: { type: Boolean, default: false },
  className: { type: String,  default: '' },
  disabled:  { type: Boolean, default: false }
})

const attrs = useAttrs()

const buttonVariants = {
  primary:   'bg-primary text-white hover:bg-primary-700 focus:ring-primary-500 active:bg-primary-800',
  secondary: 'bg-secondary text-white hover:bg-secondary-700 focus:ring-secondary-500 active:bg-secondary-800',
  outline:   'border-2 border-primary text-primary hover:bg-primary hover:text-white focus:ring-primary-500 active:bg-primary-700',
  ghost:     'text-primary hover:bg-primary-50 focus:ring-primary-500 active:bg-primary-100',
  danger:    'bg-danger text-white hover:bg-danger-700 focus:ring-danger-500 active:bg-danger-800'
}

const buttonSizes = {
  sm: 'px-3 py-1.5 text-sm',
  md: 'px-4 py-2 text-base',
  lg: 'px-6 py-3 text-lg'
}
</script>