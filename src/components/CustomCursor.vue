<template>
  <div
    v-if="!isMobile"
    class="fixed pointer-events-none z-[100] mix-blend-difference transition-all duration-75"
    :style="{
      left: `${cursorPosition.x}px`,
      top: `${cursorPosition.y}px`,
      transform: `translate(-50%, -50%) scale(${cursorScale})`
    }"
  >
    <div
      :class="[
        'w-4 h-4 rounded-full transition-colors duration-200',
        isHovering
          ? 'bg-white border-2 border-primary'
          : 'bg-primary'
      ]"
    />
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'CustomCursor',
  setup() {
    const cursorPosition = ref({ x: 0, y: 0 })
    const isHovering = ref(false)
    const cursorScale = ref(1)
    const isMobile = ref(false)

    const updateCursorPosition = (e) => {
      cursorPosition.value = { x: e.clientX, y: e.clientY }
    }

    const handleMouseEnter = (e) => {
      const target = e.target
      
      if (target && target instanceof Element) {
        if (target.matches('button, a, [role="button"]')) {
          isHovering.value = true
          cursorScale.value = 2
        } else if (target.matches('input, textarea')) {
          isHovering.value = true
          cursorScale.value = 1.5
        } else if (target.matches('h1, h2, h3, h4, h5, h6')) {
          isHovering.value = true
          cursorScale.value = 2.5
        }
      }
    }

    const handleMouseLeave = () => {
      isHovering.value = false
      cursorScale.value = 1
    }

    onMounted(() => {
      isMobile.value = window.innerWidth < 768

      if (!isMobile.value) {
        window.addEventListener('mousemove', updateCursorPosition)
        document.addEventListener('mouseenter', handleMouseEnter, true)
        document.addEventListener('mouseleave', handleMouseLeave, true)
      }
    })

    onUnmounted(() => {
      window.removeEventListener('mousemove', updateCursorPosition)
      document.removeEventListener('mouseenter', handleMouseEnter, true)
      document.removeEventListener('mouseleave', handleMouseLeave, true)
    })

    return {
      cursorPosition,
      isHovering,
      cursorScale,
      isMobile
    }
  }
}
</script>
