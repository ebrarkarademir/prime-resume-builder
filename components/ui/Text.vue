<!-- components/ui/Text.vue -->
<template>
<component
  :is="as"
  :class="[
    'font-sans',
    sizeClasses[size],
    weightClasses[weight],
    colorClasses[color],
    alignClasses[align],
    leadingClasses[leading],
    className
  ]"
>
    <slot />
  </component>
</template>

<script setup>

const props = defineProps({
  as:       { type: String,  default: 'p' },
  className:{ type: String,  default: '' },
  size:     { type: String,  default: 'base' },
  weight:   { type: String,  default: 'normal' },
  color:    { type: String,  default: 'default' },
  align:    { type: String,  default: 'left' },
  leading:  { type: String,  default: 'normal' }
})

const sizeClasses = {
  xs: 'text-xs',
  sm: 'text-sm',
  base: 'text-base',
  lg: 'text-lg',
  xl: 'text-xl'
}

const weightClasses = {
  normal: 'font-normal',
  medium: 'font-medium',
  semibold: 'font-semibold',
  bold: 'font-bold'
}

const colorClasses = {
  default:   'text-foreground',
  muted:     'text-neutral-600',
  primary:   'text-primary',
  secondary: 'text-secondary',
  success:   'text-success',
  danger:    'text-danger'
}

const alignClasses = {
  left:    'text-left',
  center:  'text-center',
  right:   'text-right',
  justify: 'text-justify'
}

const leadingClasses = {
  tight:   'leading-tight',
  snug:    'leading-snug',
  normal:  'leading-normal',
  relaxed: 'leading-relaxed',
  loose:   'leading-loose'
}
</script>