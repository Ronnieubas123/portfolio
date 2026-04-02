<template>
  <header
    v-motion
    :initial="{ y: -100 }"
    :enter="{ y: 0, transition: { duration: 600 } }"
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-500',
      scrolled 
        ? 'bg-background/80 backdrop-blur-xl border-b border-border/20 shadow-lg' 
        : 'bg-transparent'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <a href="#" class="relative group">
            <div class="flex items-center space-x-2">
              <div class="w-8 h-8 bg-primary rounded-lg flex items-center justify-center">
                <span class="text-primary-foreground font-bold text-lg">RU</span>
              </div>
              <span class="text-xl font-bold text-foreground group-hover:text-primary transition-colors">
                Ronnie Ubas
              </span>
            </div>
          </a>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden md:block">
          <div class="flex items-center space-x-8">
            <div
              v-for="(item, index) in navItems"
              :key="item.href"
              v-motion
              :initial="{ opacity: 0, y: -20 }"
              :enter="{ opacity: 1, y: 0, transition: { duration: 400, delay: index * 100 } }"
            >
              <a
                :href="item.href"
                class="group relative flex items-center gap-1 text-foreground hover:text-primary transition-colors duration-300 py-2"
              >
                <span class="relative">
                  {{ item.label }}
                  <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-primary group-hover:w-full transition-all duration-300"></span>
                </span>
              </a>
            </div>
            
            <!-- Theme Toggle -->
            <div
              v-motion
              :initial="{ opacity: 0, scale: 0.8 }"
              :enter="{ opacity: 1, scale: 1, transition: { duration: 400, delay: 400 } }"
            >
              <ThemeToggle />
            </div>
            
            <div
              v-motion
              :initial="{ opacity: 0, scale: 0.8 }"
              :enter="{ opacity: 1, scale: 1, transition: { duration: 400, delay: 500 } }"
            >
              <a
                href="#contact"
                class="bg-primary hover:bg-primary/90 text-primary-foreground px-6 py-3 rounded-full transition-all duration-300 hover:shadow-lg hover:scale-105"
              >
                Let's Talk
              </a>
            </div>
          </div>
        </nav>

        <!-- Mobile menu button -->
        <div class="md:hidden flex items-center gap-3">
          <ThemeToggle />
          <button
            @click="isMenuOpen = !isMenuOpen"
            class="relative w-10 h-10 bg-primary/10 hover:bg-primary/20 rounded-lg flex items-center justify-center transition-colors duration-300"
          >
            <transition
              mode="out-in"
              enter-active-class="transition-all duration-200"
              leave-active-class="transition-all duration-200"
              enter-from-class="rotate-90 opacity-0"
              enter-to-class="rotate-0 opacity-100"
              leave-from-class="rotate-0 opacity-100"
              leave-to-class="-rotate-90 opacity-0"
            >
              <svg v-if="isMenuOpen" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
              <svg v-else class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              </svg>
            </transition>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Navigation -->
    <transition
      enter-active-class="transition-all duration-300 ease-in-out"
      leave-active-class="transition-all duration-300 ease-in-out"
      enter-from-class="opacity-0 max-h-0"
      enter-to-class="opacity-100 max-h-96"
      leave-from-class="opacity-100 max-h-96"
      leave-to-class="opacity-0 max-h-0"
    >
      <div v-show="isMenuOpen" class="md:hidden bg-background/95 backdrop-blur-xl border-b border-border/20 overflow-hidden">
        <div class="px-4 py-6 space-y-4">
          <a
            v-for="(item, index) in navItems"
            :key="item.href"
            :href="item.href"
            @click="isMenuOpen = false"
            class="block text-lg text-foreground hover:text-primary transition-colors duration-300 py-2 border-b border-border/20"
          >
            {{ item.label }}
          </a>
          <a
            href="#contact"
            @click="isMenuOpen = false"
            class="inline-block bg-primary text-primary-foreground px-6 py-3 rounded-full mt-4"
          >
            Let's Talk
          </a>
        </div>
      </div>
    </transition>
  </header>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'
import ThemeToggle from './ThemeToggle.vue'

export default {
  name: 'Header',
  components: {
    ThemeToggle
  },
  setup() {
    const isMenuOpen = ref(false)
    const scrolled = ref(false)

    const navItems = [
      { href: '#about', label: 'About' },
      { href: '#skills', label: 'Skills' },
      { href: '#projects', label: 'Projects' },
      { href: '#contact', label: 'Contact' }
    ]

    const handleScroll = () => {
      scrolled.value = window.scrollY > 50
    }

    onMounted(() => {
      window.addEventListener('scroll', handleScroll)
    })

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll)
    })

    return {
      isMenuOpen,
      scrolled,
      navItems
    }
  }
}
</script>
