<template>
  <header :class="['bg-surface-brand border-b border-ui-brand sticky top-0 z-[1020] bg-[rgb(59,130,246)]', className]">
    <Container>
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <NuxtLink to="/" class="flex items-center space-x-2 text-white">
          <div class="w-8 h-8 bg-gradient-to-br from-accent-500 to-accent-600 rounded-lg flex items-center justify-center">
            <Text as="span" size="sm" weight="bold" >
              PR
            </Text>
          </div>
          <Text as="span" size="lg" weight="bold" class="text-content-inverse">
            PrimeResume
          </Text>
        </NuxtLink>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center space-x-8 text-white">
          <NuxtLink
            v-for="item in navigation"
            :key="item.name"
            :to="item.href"
            class="text-content-inverse text-opacity-80 hover:text-content-inverse hover:text-opacity-100 transition-fast font-medium"
          >
            {{ item.name }}
          </NuxtLink>
        </nav>

        <!-- Desktop CTA -->
        <div class="hidden md:flex items-center space-x-4 text-white">
          <Button variant="outline" size="sm" class="border-content-inverse border-opacity-30 text-content-inverse hover:bg-content-inverse hover:bg-opacity-10">
            Sign In
          </Button>
          <Button size="sm" class="bg-accent-800 text-white hover:bg-accent-700">
            Get Started
          </Button>
        </div>

        <!-- Mobile Menu Button -->
        <button
          class="md:hidden p-2 rounded-lg text-content-inverse text-opacity-80 hover:text-content-inverse hover:bg-content-inverse hover:bg-opacity-10 transition-fast touch-manipulation"
          @click="toggleMobileMenu"
          :aria-label="isMobileMenuOpen ? 'Close mobile menu' : 'Open mobile menu'"
          :aria-expanded="isMobileMenuOpen"
          aria-controls="mobile-menu"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              v-if="isMobileMenuOpen"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <div
        v-if="isMobileMenuOpen"
        id="mobile-menu"
        class="md:hidden py-4 border-t border-ui-brand border-opacity-30"
        role="navigation"
        aria-label="Mobile navigation"
      >
        <nav class="flex flex-col space-y-4">
          <NuxtLink
            v-for="item in navigation"
            :key="item.name"
            :to="item.href"
            class="text-content-inverse text-opacity-80 hover:text-content-inverse hover:text-opacity-100 transition-fast font-medium px-2 py-1"
            @click="closeMobileMenu"
          >
            {{ item.name }}
          </NuxtLink>

          <div class="flex flex-col space-y-2 pt-4 border-t border-ui-brand border-opacity-30">
            <Button variant="outline" size="sm" class="border-content-inverse border-opacity-30 text-content-inverse hover:bg-content-inverse hover:bg-opacity-10">
              Sign In
            </Button>
            <Button size="sm" class="bg-accent-600 text-white hover:bg-accent-700">
              Get Started
            </Button>
          </div>
        </nav>
      </div>
    </Container>
  </header>
</template>

<script setup>
import { ref } from 'vue';
import Container from '~/components/ui/Container.vue';
import Button from '~/components/ui/Button.vue';
import Text from '~/components/ui/Text.vue';
import { defineProps } from 'vue';

const props = defineProps({
  className: {
    type: String,
    default: ''
  }
});

const navigation = [
  { name: 'Home', href: '/' },
  { name: 'CV Editor', href: '/cv-editor' },
  { name: 'Templates', href: '#templates' },
  { name: 'Pricing', href: '#pricing' }
];

const isMobileMenuOpen = ref(false);

function toggleMobileMenu() {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
}

function closeMobileMenu() {
  isMobileMenuOpen.value = false;
}
</script>