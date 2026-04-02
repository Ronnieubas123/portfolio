<template>
  <section id="contact" class="py-32 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-background to-muted/20">
    <div class="max-w-5xl mx-auto">

      <!-- Section Header -->
      <div
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :visible-once="{ opacity: 1, y: 0, transition: { duration: 800 } }"
        class="text-center mb-16"
      >
        <div class="inline-flex items-center gap-4 text-muted-foreground mb-6">
          <div class="w-12 h-px bg-primary"></div>
          <span class="text-sm tracking-widest uppercase">Get In Touch</span>
          <div class="w-12 h-px bg-primary"></div>
        </div>

        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-foreground mb-6">
          Let’s Build Something <span class="text-primary">Great</span>
        </h2>

        <p class="text-xl text-muted-foreground max-w-3xl mx-auto">
          Open to new opportunities, collaborations, and interesting projects. If you'd like to work together or discuss a role, feel free to reach out.
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-12">

        <!-- Contact Form -->
        <div
          v-motion
          :initial="{ opacity: 0, x: -50 }"
          :visible-once="{ opacity: 1, x: 0, transition: { duration: 800 } }"
          class="bg-card border border-border rounded-2xl p-8 shadow-xl"
        >
          <img src="../assets/img/getintouuch.jpg"/>
        </div>

        <!-- Contact Info -->
        <div
          v-motion
          :initial="{ opacity: 0, x: 50 }"
          :visible-once="{ opacity: 1, x: 0, transition: { duration: 800, delay: 200 } }"
          class="space-y-8"
        >

          <div class="space-y-6">
            <div
              v-for="(info, index) in contactInfo"
              :key="index"
              class="flex items-start gap-4 p-6 bg-card border border-border rounded-xl hover:shadow-lg transition-all"
            >
              <div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center flex-shrink-0">
                <component :is="info.icon" class="h-6 w-6 text-primary" />
              </div>

              <div>
                <h3 class="font-medium text-foreground mb-1">{{ info.label }}</h3>
                <p class="text-muted-foreground">{{ info.value }}</p>
              </div>
            </div>
          </div>

          <!-- Social Links -->
          <div class="bg-gradient-to-br from-primary/10 to-chart-1/10 rounded-2xl p-8">
            <h3 class="text-xl font-bold text-foreground mb-6">Follow Me</h3>
            <div class="flex gap-4">
              <a
                v-for="social in socialLinks"
                :key="social.name"
                :href="social.url"
                target="_blank"
                class="w-12 h-12 bg-background hover:bg-primary hover:text-primary-foreground rounded-lg flex items-center justify-center transition-all hover:scale-110"
              >
                <component :is="social.icon" class="h-5 w-5" />
              </a>
            </div>
          </div>

          <!-- Availability -->
          <div class="bg-card border border-border rounded-xl p-6">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
              <span class="font-medium text-foreground">Available for new projects</span>
            </div>
            <p class="text-sm text-muted-foreground">
              Currently accepting freelance projects and consulting opportunities
            </p>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, h } from 'vue'

function createIcon(svgAttrs, paths) {
  return {
    render() {
      return h('svg', svgAttrs, paths.map(p => h('path', p)))
    }
  }
}

const MailIcon = createIcon(
  { fill: 'none', viewBox: '0 0 24 24', stroke: 'currentColor' },
  [
    {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z'
    }
  ]
)

const PhoneIcon = createIcon(
  { fill: 'none', viewBox: '0 0 24 24', stroke: 'currentColor' },
  [
    {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z'
    }
  ]
)

const LocationIcon = createIcon(
  { fill: 'none', viewBox: '0 0 24 24', stroke: 'currentColor' },
  [
    {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z'
    },
    {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M15 11a3 3 0 11-6 0 3 3 0 016 0z'
    }
  ]
)

export default {
  name: 'Contact',
  setup() {
    const formData = ref({
      name: '',
      email: '',
      subject: '',
      message: ''
    })

    const contactInfo = [
      { label: 'Email', value: 'ronnieubas123@gmail.com', icon: MailIcon },
      { label: 'Phone', value: '+639302040221', icon: PhoneIcon },
      { label: 'Location', value: 'Bacolod City, Negros Occidental Philippines', icon: LocationIcon }
    ]

    const socialLinks = []

    const handleSubmit = () => {
      console.log('Form submitted:', formData.value)
      alert('Thank you for your message! I will get back to you soon.')
      formData.value = { name: '', email: '', subject: '', message: '' }
    }

    return { formData, contactInfo, socialLinks, handleSubmit }
  }
}
</script>