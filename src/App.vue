<template>
  <div :class="{ 'dark': isDark }" class="min-h-screen bg-background overflow-x-hidden">
    <LoadingScreen />
    <ScrollProgress />
    <CustomCursor />
    <KeyboardShortcuts />
    
    <router-view />
  </div>
</template>

<script>
import { ref, provide, watch, onMounted } from 'vue'
import { useStorage } from '@vueuse/core'
import LoadingScreen from '@/components/LoadingScreen.vue'
import ScrollProgress from '@/components/ScrollProgress.vue'
import CustomCursor from '@/components/CustomCursor.vue'
import KeyboardShortcuts from '@/components/KeyboardShortcuts.vue'

export default {
  name: 'App',
  components: {
    LoadingScreen,
    ScrollProgress,
    CustomCursor,
    KeyboardShortcuts
  },
  setup() {
    const theme = useStorage('portfolio-theme', 'system')
    const isDark = ref(false)

    const updateTheme = () => {
      const root = window.document.documentElement
      let resolvedTheme = 'light'

      if (theme.value === 'system') {
        resolvedTheme = window.matchMedia('(prefers-color-scheme: dark)').matches
          ? 'dark'
          : 'light'
      } else {
        resolvedTheme = theme.value
      }

      isDark.value = resolvedTheme === 'dark'
    }

    const setTheme = (newTheme) => {
      theme.value = newTheme
      updateTheme()
    }

    watch(theme, updateTheme)

    onMounted(() => {
      updateTheme()
      
      // Listen for system theme changes
      const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)')
      mediaQuery.addEventListener('change', () => {
        if (theme.value === 'system') {
          updateTheme()
        }
      })
    })

    // Provide theme context to all child components
    provide('theme', {
      theme,
      isDark,
      setTheme
    })

    return {
      isDark
    }
  }
}
</script>
