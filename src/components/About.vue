<template>
  <section id="about" class="py-32 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-background to-muted/20">
    <div class="max-w-7xl mx-auto">
      <!-- Section Header -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="text-center mb-20"
      >
        <div class="inline-flex items-center gap-4 text-muted-foreground mb-6">
          <div class="w-12 h-px bg-primary"></div>
          <span class="text-sm tracking-widest uppercase">About Me</span>
          <div class="w-12 h-px bg-primary"></div>
        </div>
        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-foreground mb-6">
          Crafting Digital
          <span class="text-primary block">Experiences</span>
        </h2>
        <p class="text-xl text-muted-foreground max-w-3xl mx-auto leading-relaxed">
          Full-stack web developer with 5+ years of experience delivering scalable web solutions.
        </p>
      </div>

      <!-- Main Content Grid -->
      <div class="grid lg:grid-cols-2 gap-16 items-center mb-20">
        <!-- Left Column - Image and Stats -->
        <div
          v-motion
          :initial="{ opacity: 0, x: -50 }"
          :visible-once="{ opacity: 1, x: 0, transition: { duration: 800 } }"
          class="space-y-8"
        >
          <div class="relative">
            <div class="absolute inset-0 bg-gradient-to-br from-primary/20 to-chart-1/20 rounded-3xl transform rotate-3"></div>
            <div class="relative bg-card rounded-3xl p-8 shadow-xl">
              <img
                src="../assets/img/profile.jpg"
                alt="Alex Chen"
                class="w-full h-80 object-cover rounded-2xl mb-6"
              />
              <div class="grid grid-cols-2 gap-4">
                <div
                  v-for="(stat, index) in stats"
                  :key="index"
                  v-motion
                  :initial="{ opacity: 0, y: 20 }"
                  :visible-once="{ opacity: 1, y: 0, transition: { duration: 500, delay: index * 100 } }"
                  class="text-center"
                >
                  <div :class="['text-2xl font-bold', stat.color]">{{ stat.number }}</div>
                  <div class="text-sm text-muted-foreground">{{ stat.label }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column - Content -->
        <div
          v-motion
          :initial="{ opacity: 0, x: 50 }"
          :visible-once="{ opacity: 1, x: 0, transition: { duration: 800, delay: 200 } }"
          class="space-y-8"
        >
          <div class="space-y-6">
            <p class="text-lg text-foreground leading-relaxed">
              I specialize in developing end-to-end web solutions with a strong focus on clean code, 
              performance, and long-term maintainability. With experience in both frontend and backend 
              development, I build scalable and production-ready applications while accurately translating 
              design mockups into responsive, high-quality user interfaces.
            </p>
            <p class="text-lg text-muted-foreground leading-relaxed">
              Throughout my career, I have developed enterprise-level systems including 
              Point-of-Sale (POS) platforms, Attendance Management Systems, and ATS/CRM solutions 
              built using the PEVN stack. I have also implemented AI-driven features such as resume 
              parsing, structured data extraction, and semantic matching to enhance recruitment and business workflows. 
              Additionally, I have worked on eCommerce platforms (Magento and WooCommerce) 
              and advanced custom WordPress applications, collaborating with remote international teams to deliver 
              reliable solutions aligned with technical standards and business objectives.
            </p>
          </div>

          <div class="flex flex-wrap gap-3">
            <span
              v-for="(trait, index) in traits"
              :key="index"
              class="px-4 py-2 text-base bg-secondary text-secondary-foreground rounded-lg"
            >
              {{ trait }}
            </span>
          </div>
        </div>
      </div>

      <!-- Values Section -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="space-y-12"
      >
        <div class="text-center">
          <h3 class="text-3xl font-bold text-foreground mb-4">My Core Values</h3>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            The principles that guide my work and drive every decision I make
          </p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div
            v-for="(value, index) in values"
            :key="index"
            v-motion
            :initial="{ opacity: 0, y: 30 }"
            :visible-once="{ opacity: 1, y: 0, transition: { duration: 600, delay: index * 200 } }"
            :hovered="{ y: -5 }"
            class="h-full border-0 bg-gradient-to-br from-card to-accent/10 hover:shadow-xl transition-all duration-300 rounded-lg"
          >
            <div class="p-8 text-center space-y-4">
              <div class="text-4xl mb-4">{{ value.icon }}</div>
              <h4 class="text-xl font-bold text-foreground">{{ value.title }}</h4>
              <p class="text-muted-foreground leading-relaxed">{{ value.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  setup() {
    const stats = [
      { number: "40+", label: "Projects Delivered", color: "text-chart-1" },
      { number: "30+", label: "Happy Clients", color: "text-chart-2" },
      { number: "5+", label: "Years Experience", color: "text-chart-3" },
      { number: "10+", label: "Technologies", color: "text-chart-4" }
    ]

    const traits = [
      'Problem Solver',
      'Solution Driven',
      'Detail Oriented',
      'Team Player'
    ]

    const values = [
      {
        title: "Strategic Problem Solving",
        description: "Approaching complex requirements with analytical thinking and translating them into scalable, reliable technical solutions.",
        icon: "🧠"
      },
      {
        title: "Performance & Scalability",
        description: "Building optimized systems with clean architecture designed for long-term growth and high performance.",
        icon: "⚡"
      },
      {
        title: "Continuous Evolution",
        description: "Constantly advancing in AI integration, automation, and modern frameworks to stay ahead of industry trends.",
        icon: "🤖"
      }
    ]

    return {
      stats,
      traits,
      values
    }
  }
}
</script>
