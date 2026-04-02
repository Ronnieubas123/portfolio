<template>
  <div>
    <Header />
    <main>
      <Hero />
      <About />
      <Skills />
      <Experience />
      <Projects />
      <Contact />
    </main>
    <Footer />
    <FloatingActions />
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Hero from '@/components/Hero.vue'
import About from '@/components/About.vue'
import Skills from '@/components/Skills.vue'
import Experience from '@/components/Experience.vue'
import Projects from '@/components/Projects.vue'
import Contact from '@/components/Contact.vue'
import Footer from '@/components/Footer.vue'
import FloatingActions from '@/components/FloatingActions.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Hero,
    About,
    Skills,
    Experience,
    Projects,
    Contact,
    Footer,
    FloatingActions
  }
}
</script>
