<template>
  <div class="relative">
    <!-- Toggle Button -->
    <button
      @click="toggle"
      class="relative w-10 h-10 p-0 bg-background/50 backdrop-blur-sm border border-border/50 hover:bg-accent/50 rounded-md transition-colors inline-flex items-center justify-center"
    >
      <transition
        mode="out-in"
        enter-active-class="transition-all duration-200"
        leave-active-class="transition-all duration-200"
        enter-from-class="scale-0 -rotate-180"
        enter-to-class="scale-100 rotate-0"
        leave-from-class="scale-100 rotate-0"
        leave-to-class="scale-0 rotate-180"
      >
        <!-- Dark Icon -->
        <svg
          v-if="isDark"
          key="moon"
          class="h-4 w-4"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"
          />
        </svg>

        <!-- Light Icon -->
        <svg
          v-else
          key="sun"
          class="h-4 w-4"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"
          />
        </svg>
      </transition>
    </button>

    <!-- Dropdown -->
    <transition
      enter-active-class="transition-all duration-200"
      leave-active-class="transition-all duration-200"
      enter-from-class="opacity-0 scale-95 -translate-y-2"
      enter-to-class="opacity-100 scale-100 translate-y-0"
      leave-from-class="opacity-100 scale-100 translate-y-0"
      leave-to-class="opacity-0 scale-95 -translate-y-2"
    >
      <div
        v-show="isOpen"
        class="absolute right-0 mt-2 w-36 bg-card/95 backdrop-blur-sm border border-border/50 rounded-md shadow-lg overflow-hidden z-50"
      >
        <button
          v-for="option in themes"
          :key="option.value"
          @click="selectTheme(option.value)"
          :class="[
            'w-full px-4 py-2 text-left hover:bg-accent transition-colors flex items-center gap-2',
            theme === option.value ? 'bg-accent' : ''
          ]"
        >
          <span>{{ option.label }}</span>

          <div
            v-if="theme === option.value"
            class="ml-auto w-2 h-2 bg-primary rounded-full"
          ></div>
        </button>
      </div>
    </transition>
  </div>
</template>

<script>
import { ref, computed, onMounted, onUnmounted } from 'vue'

export default {
  name: 'ThemeToggle',

  setup() {
    const isOpen = ref(false)
    const theme = ref(localStorage.getItem('theme') || 'system')

    const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)')

    const applyTheme = (value) => {
      if (value === 'dark') {
        document.documentElement.classList.add('dark')
      } else if (value === 'light') {
        document.documentElement.classList.remove('dark')
      } else {
        // system
        document.documentElement.classList.toggle(
          'dark',
          mediaQuery.matches
        )
      }
    }

    const setTheme = (value) => {
      theme.value = value
      localStorage.setItem('theme', value)
      applyTheme(value)
    }

    const selectTheme = (value) => {
      setTheme(value)
      isOpen.value = false
    }

    const isDark = computed(() => {
      if (theme.value === 'dark') return true
      if (theme.value === 'light') return false
      return mediaQuery.matches
    })

    const toggle = () => {
      isOpen.value = !isOpen.value
    }

    // Click outside handler
    const wrapper = ref(null)

    const handleClickOutside = (event) => {
      if (wrapper.value && !wrapper.value.contains(event.target)) {
        isOpen.value = false
      }
    }

    // System theme listener
    const handleSystemChange = () => {
      if (theme.value === 'system') {
        applyTheme('system')
      }
    }

    onMounted(() => {
      applyTheme(theme.value)
      document.addEventListener('click', handleClickOutside)
      mediaQuery.addEventListener('change', handleSystemChange)
    })

    onUnmounted(() => {
      document.removeEventListener('click', handleClickOutside)
      mediaQuery.removeEventListener('change', handleSystemChange)
    })

    const themes = [
      { value: 'light', label: 'Light' },
      { value: 'dark', label: 'Dark' },
      { value: 'system', label: 'System' }
    ]

    return {
      isOpen,
      theme,
      themes,
      isDark,
      toggle,
      selectTheme,
      wrapper
    }
  }
}
</script>