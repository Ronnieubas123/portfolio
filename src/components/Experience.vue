<template>
  <section id="experience" class="py-32 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-muted/20 to-background">
    <div class="max-w-5xl mx-auto">
      <!-- Section Header -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="text-center mb-20"
      >
        <div class="inline-flex items-center gap-4 text-muted-foreground mb-6">
          <div class="w-12 h-px bg-primary"></div>
          <span class="text-sm tracking-widest uppercase">Experience</span>
          <div class="w-12 h-px bg-primary"></div>
        </div>
        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-foreground mb-6">
          Career <span class="text-primary">Journey</span>
        </h2>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <!-- Timeline Line -->
        <div class="absolute left-8 md:left-1/2 top-0 bottom-0 w-0.5 bg-gradient-to-b from-primary via-chart-1 to-chart-2"></div>

        <!-- Experience Items -->
        <div class="space-y-12">
          <div
            v-for="(exp, index) in experiences"
            :key="index"
            v-motion
            :initial="{ opacity: 0, x: index % 2 === 0 ? -50 : 50 }"
            :visible-once="{ opacity: 1, x: 0, transition: { duration: 600, delay: index * 200 } }"
            :class="[
              'relative flex items-center',
              index % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'
            ]"
          >
            <!-- Timeline Dot -->
            <div class="absolute left-8 md:left-1/2 w-4 h-4 bg-primary rounded-full border-4 border-background transform -translate-x-1/2 z-10"></div>

            <!-- Content Card -->
            <div :class="['w-full md:w-[calc(50%-3rem)]', index % 2 === 0 ? 'md:pr-12' : 'md:pl-12']">
              <div class="ml-16 md:ml-0 bg-card border border-border rounded-2xl p-6 hover:shadow-xl transition-all duration-300">
                <div class="flex items-start justify-between mb-4">
                  <div>
                    <h3 class="text-xl font-bold text-foreground mb-1">{{ exp.title }}</h3>
                    <p class="text-primary font-medium">{{ exp.company }}</p>
                  </div>
                  <span class="px-3 py-1 bg-primary/10 text-primary rounded-full text-sm whitespace-nowrap">
                    {{ exp.period }}
                  </span>
                </div>
                <p class="text-muted-foreground mb-4">{{ exp.description }}</p>
                <div class="flex flex-wrap gap-2">
                  <span
                    v-for="tech in exp.technologies"
                    :key="tech"
                    class="px-3 py-1 bg-accent text-accent-foreground rounded-lg text-sm"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Experience',
  setup() {
    const experiences = [
    {
      title: "Full-Stack Developer",
      company: "Xulvar",
      period: "08/2025 - 04/2026",
      description: "Designed and developed a full-featured Applicant Tracking System (ATS) and CRM platform using the PEVN stack. Implemented AI-powered resume parsing and semantic candidate-job matching to streamline recruitment processes.",
      technologies: ["Vue.js", "Express.js", "PostgreSQL", "Node.js", "Tailwind", "SendGrid","Twilio", "AI Integration", "HTML", "Vite", "RestApi"]
    },
    {
      title: "WordPress Developer",
      company: "MSB8 Developer",
      period: "02/2025 - 07/2025",
      description: "Built custom WordPress websites and landing pages using Elementor, Divi, JetEngine, and advanced PHP customization beyond standard builder limitations. Focused on performance optimization and responsive design.",
      technologies: ["WordPress", "Elementor", "Divi", "JetEngine", "PHP", "CSS", "JavaScript", "jQuery", "HTML", "ACF"]
    },
    {
      title: "Web Developer",
      company: "Growmodo",
      period: "09/2023 - 01/2025",
      description: "Developed responsive websites and landing pages for international clients, ensuring high performance, clean UI implementation, and delivery under tight deadlines.",
      technologies: ["WordPress", "Webflow", "Elementor", "Divi", "WPBakery", 
      "PEVN Stack", "Tailwind CSS", "JavaScript", "jQuery", "CSS", "HTML", "GSAP", "MongoDB", "Vite", "RestApi", "JetEngine", "ACF"]
    },
    {
      title: "Web Developer",
      company: "Capella BPO",
      period: "03/2023 - 08/2023",
      description: "Developed an AI-driven health inquiry platform and an eBook sales website using WordPress, focusing on automation, usability, and system efficiency.",
      technologies: ["WordPress", "Elementor", "PEVN Stack", "MongoDB", "AI Integration", "RestApi", "Langchain", "10Web", "WooCommerce", "Tailwind CSS", "JavaScript", "jQuery", "CSS", "HTML", "Vite"]
    },
    {
      title: "WordPress & WooCommerce",
      company: "WP Tangerine",
      period: "02/2021 - 02/2023",
      description: "Developed and maintained high-quality WordPress and WooCommerce websites for global clients, delivering scalable and performance-optimized solutions.",
      technologies: ["WordPress", "WooCommerce", "PHP", "JavaScript", "jQuery", "CSS", "HTML"]
    },
    {
      title: "Full-Stack Developer",
      company: "Aldrtz Corporation",
      period: "01/2020 - 01/2021",
      description: "Developed a Magento 2 multi-vendor eCommerce platform, a WooCommerce website, and an internal attendance monitoring system to improve operational workflow.",
      technologies: ["Magento 2", "WordPress", "WooCommerce", "PHP", "MySQL", "CSS", "Bootstrap", "HTML", "Laravel", "RestApi"]
    }
  ]

    return {
      experiences
    }
  }
}
</script>
