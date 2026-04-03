<template>
  <section id="skills" class="py-32 px-4 sm:px-6 lg:px-8 bg-background">
    <div class="max-w-7xl mx-auto">
      <!-- Section Header -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="text-center mb-16"
      >
        <div class="inline-flex items-center gap-4 text-muted-foreground mb-6">
          <div class="w-12 h-px bg-primary"></div>
          <span class="text-sm tracking-widest uppercase">Skills & Expertise</span>
          <div class="w-12 h-px bg-primary"></div>
        </div>
        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-foreground mb-6">
          Technical <span class="text-primary">Arsenal</span>
        </h2>
        <p class="text-xl text-muted-foreground max-w-3xl mx-auto">
          A comprehensive toolkit built over years of professional experience
        </p>
      </div>

      <!-- Category Tabs -->
      <div class="flex flex-wrap justify-center gap-4 mb-12">
        <button
          v-for="(category, key) in skillCategories"
          :key="key"
          @click="activeCategory = key"
          :class="[
            'px-6 py-3 rounded-full transition-all duration-300 font-medium',
            activeCategory === key
              ? 'bg-primary text-primary-foreground shadow-lg scale-105'
              : 'bg-muted text-muted-foreground hover:bg-accent'
          ]"
        >
          {{ category.title }}
        </button>
      </div>

      <!-- Skills Grid -->
      <transition
        mode="out-in"
        enter-active-class="transition-all duration-300"
        leave-active-class="transition-all duration-300"
        enter-from-class="opacity-0 translate-y-4"
        enter-to-class="opacity-100 translate-y-0"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-4"
      >
        <div :key="activeCategory" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mb-20">
          <div
            v-for="(skill, index) in skillCategories[activeCategory].skills"
            :key="skill.name"
            v-motion
            :initial="{ opacity: 0, scale: 0.9 }"
            :visible-once="{ opacity: 1, scale: 1, transition: { duration: 400, delay: index * 50 } }"
            class="bg-card border border-border rounded-xl p-6 hover:shadow-lg hover:-translate-y-1 transition-all duration-300"
          >
            <div class="flex items-start justify-between mb-4">
              <div class="flex items-center gap-3">
                <span class="text-3xl">{{ skill.icon }}</span>
                <div>
                  <h3 class="text-lg font-bold text-foreground">{{ skill.name }}</h3>
                  <p class="text-sm text-muted-foreground">{{ skill.experience }}</p>
                </div>
              </div>
            </div>
            <span
              :class="[
                'inline-block px-3 py-1 rounded-full text-xs font-medium border',
                getLevelColor(skill.level)
              ]"
            >
              {{ skill.level }}
            </span>
          </div>
        </div>
      </transition>

      <!-- Tools & Technologies -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="space-y-8"
      >
        <div class="text-center">
          <h3 class="text-3xl font-bold text-foreground mb-4">Tools & Technologies</h3>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            Daily tools that power my development workflow
          </p>
        </div>

        <div class="flex flex-wrap justify-center gap-4">
          <div
            v-for="(tool, index) in tools"
            :key="tool.name"
            v-motion
            :initial="{ opacity: 0, scale: 0.8 }"
            :visible-once="{ opacity: 1, scale: 1, transition: { duration: 300, delay: index * 30 } }"
            class="group relative px-5 py-3 bg-gradient-to-br from-card to-accent/10 border border-border rounded-lg hover:shadow-md hover:border-primary/50 transition-all duration-300"
          >
            <div class="font-medium text-foreground">{{ tool.name }}</div>
            <div class="text-xs text-muted-foreground">{{ tool.category }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'Skills',
  setup() {
    const activeCategory = ref('frontend')

    const skillCategories = {
      frontend: {
        title: "Frontend Development",
        color: "from-chart-1 to-chart-2",
        skills: [
          { name: "React", experience: "4+ months", level: "Beginner", icon: "⚛️" },
          { name: "Vue.js", experience: "3+ years", level: "Expert", icon: "💚" },
          { name: "Webflow", experience: "1+ year", level: "Intermediate", icon: "🖥️" },
          { name: "JavaScript", experience: "7+ years", level: "Expert", icon: "🟨" },
          { name: "Ionic Framework", experience: "3+ months", level: "Beginner", icon: "📱" },
          { name: "Tailwind CSS", experience: "3+ years", level: "Advanced", icon: "🌬️" },
          { name: "HTML5.js", experience: "7+ years", level: "Expert", icon: "▲" },
          { name: "CSS", experience: "7+ years", level: "Expert", icon: "🎨" },
          { name: "Bootstrap", experience: "1+ year", level: "Intermediate", icon: "🅱️" },
          { name: "jQuery", experience: "7+ years", level: "Intermediate", icon: "📜" },
          { name: "LESS", experience: "1+ year", level: "Advanced", icon: "🧩" },
          { name: "GSAP", experience: "2+ years", level: "Advanced", icon: "🎞️" }  
        ]
      },
      backend: {
        title: "Backend Development", 
        color: "from-chart-3 to-chart-4",
        skills: [
          { name: "PHP", experience: "4+ years", level: "Expert", icon: "🐘" },
          { name: "Node.js", experience: "3+ years", level: "Expert", icon: "🟢" },
          { name: "Express.js", experience: "3+ years", level: "Expert", icon: "🟢" },
          { name: "MongoDB", experience: "3+ years", level: "Expert", icon: "🍃" },
          { name: "Laravel", experience: "2+ years", level: "Advanced", icon: "🏗️" },
          { name: "REST APIs", experience: "5+ years", level: "Expert", icon: "🔗" },
          { name: "MySQL", experience: "4+ years", level: "Intermediate", icon: "🗄️" },
          { name: "Magento 2", experience: "1+ year", level: "Advanced", icon: "🛒" },
          { name: "Aimeos", experience: "1+ year", level: "Beginner", icon: "🛍️" },
          { name: "WordPress", experience: "5+ years", level: "Expert", icon: "📝" },
        ]
      },
      devops: {
        title: "DevOps & Cloud",
        color: "from-chart-5 to-primary",
        skills: [
          { name: "AWS", experience: "2+ months", level: "Beginner", icon: "☁️" },
          { name: "CI/CD", experience: "3+ years", level: "Advanced", icon: "🔄" },
          { name: "Git", experience: "3+ years", level: "Expert", icon: "🌿" },
          { name: "GoDaddy", experience: "3+ years", level: "Advanced", icon: "🟡" },
          { name: "Hostinger", experience: "5+ months", level: "Intermediate", icon: "🟠" },
          { name: "SiteGround", experience: "1+ year", level: "Intermediate", icon: "🟢" },
          { name: "Bluehost", experience: "1+ year", level: "Intermediate", icon: "🔵" },
        ]
      },
      design: {
        title: "Design & UX",
        color: "from-primary to-chart-1",
        skills: [
          { name: "Figma", experience: "4+ years", level: "Advanced", icon: "🎨" },
          { name: "Adobe XD", experience: "3+ years", level: "Beginner", icon: "🟪" },
          { name: "Adobe Photoshop", experience: "3+ years", level: "Beginner", icon: "🟦" },
          { name: "Photopea", experience: "2+ years", level: "Intermediate", icon: "🟢" },
          { name: "Animation", experience: "2+ years", level: "Intermediate", icon: "🎞️" }
        ]
      }
    }

    const tools = [
      { name: "VS Code", category: "Code Editor" },
      { name: "Sublime Text", category: "Code Editor" },
      { name: "Git", category: "Version Control" },
      { name: "Postman", category: "API Testing Tool" },
      { name: "Insomnia", category: "REST Client" },
      { name: "Vite", category: "Build Tools" },
      { name: "Figma", category: "UI/UX Design Tool" },
      { name: "Adobe XD", category: "UI Design Tool" },
      { name: "Adobe Photoshop", category: "Image Editing" },
      { name: "photopea", category: "Online Image Editing" },
      { name: "Canva", category: "Graphic Design Tool" },
      { name: "cPanel", category: "Hosting Control Panel" },
      { name: "FileZilla", category: "FTP Client" },
      { name: "npm", category: "Node Package Manager" },
      { name: "Git Bash", category: "Command Line Tool" },
      { name: "Terminal", category: "Command Line Interface" },
      { name: "Notion", category: "Documentation & Workspace Tool" },
      { name: "Slack", category: "Team Communication Tool" },
      { name: "Mailchimp", category: "Email Marketing Platform" },
      { name: "Basecamp", category: "Project Management Tool" },
      { name: "Asana", category: "Task & Workflow Management Tool" },
      
    ]

    const getLevelColor = (level) => {
      switch (level) {
        case 'Expert': return 'bg-green-100 text-green-700 border-green-200 dark:bg-green-900/30 dark:text-green-400 dark:border-green-800'
        case 'Advanced': return 'bg-blue-100 text-blue-700 border-blue-200 dark:bg-blue-900/30 dark:text-blue-400 dark:border-blue-800'
        case 'Intermediate': return 'bg-yellow-100 text-yellow-700 border-yellow-200 dark:bg-yellow-900/30 dark:text-yellow-400 dark:border-yellow-800'
        case 'Beginner': return 'bg-gray-100 text-gray-700 border-gray-200 dark:bg-gray-900/30 dark:text-gray-400 dark:border-gray-800'
        default: return 'bg-gray-100 text-gray-700 border-gray-200'
      }
    }

    return {
      activeCategory,
      skillCategories,
      tools,
      getLevelColor
    }
  }
}
</script>
