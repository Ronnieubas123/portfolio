<template>
  <div
    class="fixed top-0 left-0 right-0 h-1 bg-muted/30 z-[60]"
  >
    <div
      class="h-full bg-gradient-to-r from-primary via-chart-1 to-chart-2 transition-all duration-150 ease-out origin-left"
      :style="{ transform: `scaleX(${scrollProgress / 100})` }"
    ></div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'ScrollProgress',
  setup() {
    const scrollProgress = ref(0)

    const updateScrollProgress = () => {
      const windowHeight = window.innerHeight
      const documentHeight = document.documentElement.scrollHeight
      const scrollTop = window.scrollY
      const scrollDistance = documentHeight - windowHeight
      
      if (scrollDistance > 0) {
        scrollProgress.value = (scrollTop / scrollDistance) * 100
      }
    }

    onMounted(() => {
      window.addEventListener('scroll', updateScrollProgress)
      updateScrollProgress()
    })

    onUnmounted(() => {
      window.removeEventListener('scroll', updateScrollProgress)
    })

    return {
      scrollProgress
    }
  }
}
</script>
