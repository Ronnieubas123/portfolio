<template>
  <teleport to="body">
    <!-- Keyboard Shortcuts Modal -->
    <transition
      enter-active-class="transition-opacity duration-300"
      leave-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-show="showShortcuts"
        class="fixed inset-0 bg-black/50 backdrop-blur-sm z-[90] flex items-center justify-center p-4"
        @click="showShortcuts = false"
      >
        <div
          @click.stop
          class="bg-card border border-border rounded-2xl shadow-2xl max-w-2xl w-full max-h-[80vh] overflow-y-auto"
        >
          <div class="sticky top-0 bg-card border-b border-border px-6 py-4 flex items-center justify-between">
            <h2 class="text-2xl font-bold text-foreground">Keyboard Shortcuts</h2>
            <button
              @click="showShortcuts = false"
              class="w-8 h-8 rounded-lg hover:bg-accent transition-colors flex items-center justify-center"
            >
              <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </div>

          <div class="p-6 space-y-4">
            <div
              v-for="shortcut in shortcuts"
              :key="shortcut.key"
              class="flex items-center justify-between py-3 border-b border-border/50 last:border-0"
            >
              <span class="text-foreground">{{ shortcut.description }}</span>
              <kbd class="px-3 py-1.5 bg-muted text-muted-foreground rounded-lg font-mono text-sm border border-border">
                {{ shortcut.key }}
              </kbd>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </teleport>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'KeyboardShortcuts',
  setup() {
    const showShortcuts = ref(false)

    const shortcuts = [
      { key: '?', description: 'Show keyboard shortcuts' },
      { key: 'H', description: 'Go to top' },
      { key: 'A', description: 'Go to About section' },
      { key: 'S', description: 'Go to Skills section' },
      { key: 'P', description: 'Go to Projects section' },
      { key: 'C', description: 'Go to Contact section' },
      { key: 'T', description: 'Toggle theme' },
      { key: 'Esc', description: 'Close modals' }
    ]

    const scrollToSection = (id) => {
      const element = document.getElementById(id)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }
    }

    const handleKeyPress = (e) => {
      // Don't trigger if user is typing in an input
      if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') {
        return
      }

      switch (e.key.toLowerCase()) {
        case '?':
          e.preventDefault()
          showShortcuts.value = !showShortcuts.value
          break
        case 'h':
          e.preventDefault()
          window.scrollTo({ top: 0, behavior: 'smooth' })
          break
        case 'a':
          e.preventDefault()
          scrollToSection('about')
          break
        case 's':
          e.preventDefault()
          scrollToSection('skills')
          break
        case 'p':
          e.preventDefault()
          scrollToSection('projects')
          break
        case 'c':
          e.preventDefault()
          scrollToSection('contact')
          break
        case 'escape':
          showShortcuts.value = false
          break
      }
    }

    onMounted(() => {
      document.addEventListener('keydown', handleKeyPress)
    })

    onUnmounted(() => {
      document.removeEventListener('keydown', handleKeyPress)
    })

    return {
      showShortcuts,
      shortcuts
    }
  }
}
</script>
