<template>
  <transition
    enter-active-class="transition-opacity duration-300"
    leave-active-class="transition-opacity duration-500"
    enter-from-class="opacity-100"
    enter-to-class="opacity-100"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0"
  >
    <div
      v-show="isLoading"
      class="fixed inset-0 z-[100] bg-background flex items-center justify-center"
    >
      <div class="text-center space-y-8">
        <!-- Animated Logo -->
        <div
          v-motion
          :initial="{ scale: 0, rotate: -180 }"
          :enter="{ scale: 1, rotate: 0, transition: { duration: 800, ease: 'easeOut' } }"
          class="w-20 h-20 bg-primary rounded-2xl flex items-center justify-center mx-auto relative overflow-hidden"
        >
          <span class="text-primary-foreground font-bold text-3xl relative z-10">RU</span>
          <div class="absolute inset-0 bg-gradient-to-br from-primary to-chart-1 opacity-50 animate-pulse"></div>
        </div>

        <!-- Loading Text -->
        <div
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :enter="{ opacity: 1, y: 0, transition: { duration: 600, delay: 300 } }"
          class="space-y-2"
        >
          <h2 class="text-2xl font-bold text-foreground">Ronnie Ubas</h2>
          <p class="text-muted-foreground">Loading portfolio...</p>
        </div>

        <!-- Progress Bar -->
        <div
          v-motion
          :initial="{ opacity: 0, scale: 0.8 }"
          :enter="{ opacity: 1, scale: 1, transition: { duration: 600, delay: 500 } }"
          class="w-64 h-1.5 bg-muted rounded-full overflow-hidden mx-auto"
        >
          <div
            class="h-full bg-gradient-to-r from-primary via-chart-1 to-chart-2 transition-all duration-1000 ease-out"
            :style="{ width: `${progress}%` }"
          ></div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'LoadingScreen',
  setup() {
    const isLoading = ref(true)
    const progress = ref(0)

    onMounted(() => {
      // Simulate loading progress
      const interval = setInterval(() => {
        progress.value += 10
        if (progress.value >= 100) {
          clearInterval(interval)
          setTimeout(() => {
            isLoading.value = false
          }, 300)
        }
      }, 150)
    })

    return {
      isLoading,
      progress
    }
  }
}
</script>
