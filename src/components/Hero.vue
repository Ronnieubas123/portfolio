<template>
  <section class="relative min-h-screen overflow-hidden bg-gradient-to-br from-background via-accent/20 to-muted/30">
    <!-- Animated background elements -->
    <div class="absolute inset-0">
      <div
        v-motion
        :initial="{ x: -100, y: -100 }"
        :style="{
          transform: `translate(${mousePosition.x * 0.02}px, ${mousePosition.y * 0.02}px)`
        }"
        class="absolute w-96 h-96 rounded-full bg-gradient-to-r from-primary/10 to-chart-1/10 blur-3xl transition-transform duration-700 ease-out"
      />
      <div
        :style="{
          transform: `translate(${-mousePosition.x * 0.01}px, ${-mousePosition.y * 0.01}px)`
        }"
        class="absolute right-0 bottom-0 w-80 h-80 rounded-full bg-gradient-to-l from-chart-2/10 to-chart-3/10 blur-3xl transition-transform duration-700 ease-out"
      />
    </div>

    <!-- Geometric decorations -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-20 left-10 w-4 h-4 bg-primary rotate-45 opacity-60" />
      <div class="absolute top-40 right-20 w-6 h-6 border-2 border-chart-1 rotate-12" />
      <div class="absolute bottom-32 left-1/4 w-8 h-8 bg-chart-2 rounded-full opacity-40" />
      <div class="absolute bottom-20 right-1/3 w-3 h-16 bg-gradient-to-t from-chart-3 to-transparent opacity-50" />
    </div>

    <div class="relative z-10 flex items-center min-h-screen px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto w-full">
        <div class="grid lg:grid-cols-12 gap-8 items-center">
          <!-- Main content -->
          <div class="lg:col-span-8 space-y-8">
            <div
              v-motion
              :initial="{ opacity: 0, y: 50 }"
              :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }"
              class="space-y-6"
            >
              <div class="flex items-center gap-4 text-muted-foreground mb-4">
                <div class="w-12 h-px bg-primary"></div>
                <span class="text-sm tracking-widest uppercase">Full-Stack Web Developer</span>
              </div>
              
              <h1 class="text-5xl sm:text-6xl lg:text-7xl font-bold leading-none">
                <span class="block text-foreground">RONNIE</span>
                <span class="block text-primary font-extralight">UBAS</span>
              </h1>
              
              <p class="text-xl sm:text-2xl lg:text-3xl text-muted-foreground max-w-2xl leading-relaxed">
                I build scalable
                <span class="text-primary font-medium"> web applications, high-performance WordPress platforms,</span> and
                <span class="text-chart-1 font-medium"> AI-powered systems</span>
                that bridge business goals with modern technology.
              </p>
            </div>

            <div
              v-motion
              :initial="{ opacity: 0, y: 30 }"
              :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 300 } }"
              class="flex flex-col sm:flex-row gap-4"
            >
              <button 
                @click="scrollToSection('projects')"
                class="group bg-primary hover:bg-primary/90 text-primary-foreground px-8 py-4 rounded-full inline-flex items-center justify-center gap-2 transition-all"
              >
                <span>View Projects</span>
                <svg class="ml-2 h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                </svg>
              </button>
              <button class="border-2 border-primary text-primary hover:bg-primary hover:text-primary-foreground px-8 py-4 rounded-full inline-flex items-center justify-center gap-2 transition-all">
                <svg class="mr-2 h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
                </svg>
                <span>Download Resume</span>
              </button>
            </div>
          </div>

          <!-- Sidebar info -->
          <div class="lg:col-span-4 space-y-8">
            <div
              v-motion
              :initial="{ opacity: 0, x: 50 }"
              :enter="{ opacity: 1, x: 0, transition: { duration: 800, delay: 500 } }"
              class="bg-card/50 backdrop-blur-sm border border-border/50 rounded-2xl p-6 space-y-6"
            >
              <div>
                <h3 class="text-lg font-medium text-foreground mb-3">Currently</h3>
                <p class="text-muted-foreground">
                  Developing AI-integrated web applications and scalable WordPress platforms for <span class="text-primary">Global Clients</span>.
                </p>
                <!--<p class="text-muted-foreground mt-2">
                  Building the future of digital experiences
                </p>-->
              </div>

              <div>
                <h3 class="text-lg font-medium text-foreground mb-3">Specializing In</h3>
                <div class="flex flex-wrap gap-2">
                  <span class="px-3 py-1 bg-chart-2/10 text-primary rounded-full text-sm">WordPress Custom Development</span>
                  <span class="px-3 py-1 bg-chart-3/10 text-chart-1 rounded-full text-sm">Full-Stack Web Applications</span>
                  <span class="px-3 py-1 bg-chart-4/10 text-chart-2 rounded-full text-sm">AI Integration</span>
                  <span class="px-3 py-1 bg-chart-5/10 text-chart-3 rounded-full text-sm">eCommerce & CRM Systems</span>
                </div>
              </div>

              <div>
                <h3 class="text-lg font-medium text-foreground mb-3">Connect</h3>
                <div class="flex gap-3">
                  <a href="https://github.com" class="w-10 h-10 bg-primary/10 hover:bg-primary hover:text-primary-foreground text-primary rounded-full flex items-center justify-center transition-all duration-300">
                    <svg class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                    </svg>
                  </a>
                  <a href="https://linkedin.com" class="w-10 h-10 bg-chart-1/10 hover:bg-chart-1 hover:text-white text-chart-1 rounded-full flex items-center justify-center transition-all duration-300">
                    <svg class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                    </svg>
                  </a>
                  <a href="mailto:alex@example.com" class="w-10 h-10 bg-chart-2/10 hover:bg-chart-2 hover:text-white text-chart-2 rounded-full flex items-center justify-center transition-all duration-300">
                    <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                    </svg>
                  </a>
                </div>
              </div>
            </div>

            <div
              v-motion
              :initial="{ opacity: 0, scale: 0.8 }"
              :enter="{ opacity: 1, scale: 1, transition: { duration: 800, delay: 700 } }"
              class="text-center space-y-2"
            >
              <div class="text-3xl font-bold text-primary">5+</div>
              <div class="text-muted-foreground">Years Experience</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'Hero',
  setup() {
    const mousePosition = ref({ x: 0, y: 0 })

    const handleMouseMove = (e) => {
      mousePosition.value = { x: e.clientX, y: e.clientY }
    }

    const scrollToSection = (id) => {
      const element = document.getElementById(id)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }
    }

    onMounted(() => {
      window.addEventListener('mousemove', handleMouseMove)
    })

    onUnmounted(() => {
      window.removeEventListener('mousemove', handleMouseMove)
    })

    return {
      mousePosition,
      scrollToSection
    }
  }
}
</script>
