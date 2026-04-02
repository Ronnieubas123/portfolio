<template>
  <section id="projects" class="py-32 px-4 sm:px-6 lg:px-8 bg-background">
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
          <span class="text-sm tracking-widest uppercase">Portfolio</span>
          <div class="w-12 h-px bg-primary"></div>
        </div>

        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-foreground mb-6">
          Featured <span class="text-primary">Projects</span>
        </h2>

        <p class="text-xl text-muted-foreground max-w-3xl mx-auto">
          A selection of my recent work that showcases my skills and passion
        </p>
      </div>

      <!-- Projects Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">

        <div
          v-for="(project, index) in projects"
          :key="project.id"
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :visible-once="{ opacity: 1, y: 0, transition: { duration: 600, delay: index * 100 } }"
          @click="handleProjectClick(project)"
          class="group cursor-pointer bg-card border border-border rounded-2xl overflow-hidden hover:shadow-2xl transition-all duration-300 hover:-translate-y-2"
        >

          <!-- Project Image -->
          <div class="relative h-56 overflow-hidden">

            <img
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
            />

            <div class="absolute inset-0 bg-gradient-to-t from-card/90 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>

            <!-- Private Badge -->
            <span
              v-if="project.private"
              class="absolute top-3 right-3 bg-black/70 text-white text-xs px-3 py-1 rounded-full"
            >
              Private
            </span>

          </div>

          <!-- Project Content -->
          <div class="p-6 space-y-4">

            <div>
              <h3 class="text-xl font-bold text-foreground mb-2 group-hover:text-primary transition-colors">
                {{ project.title }}
              </h3>

              <p class="text-muted-foreground">
                {{ project.description }}
              </p>
            </div>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="px-3 py-1 bg-primary/10 text-primary rounded-lg text-sm"
              >
                {{ tech }}
              </span>
            </div>

          </div>
        </div>

      </div>
    </div>

    <!-- Private Modal -->
    <div
      v-if="showPrivateModal"
      class="fixed inset-0 flex items-center justify-center bg-black/60 z-50"
    >
      <div class="bg-card p-8 rounded-xl max-w-md text-center border border-border">

        <h3 class="text-2xl font-bold mb-4 text-foreground">
          Private System
        </h3>

        <p class="text-muted-foreground mb-6">
          This project is a proprietary internal system and cannot be publicly accessed.
          It is included in this portfolio to showcase the technologies and development
          experience involved in building enterprise-level platforms.
        </p>

        <button
          @click="showPrivateModal = false"
          class="px-6 py-2 bg-primary text-primary-foreground rounded-lg hover:bg-primary/90 transition"
        >
          Close
        </button>

      </div>
    </div>

  </section>
</template>

<script>
import { ref } from "vue"

import atsCrm from '../assets/img/ATS + CRM.PNG';
import youlink from '../assets/img/youlink.PNG';
import aihealth from '../assets/img/aihealthpro.png';
import pulseplay from '../assets/img/Pulseplay.png';
import iminsured from '../assets/img/iminsured.png';  
import omg from '../assets/img/omg.png';  
import networkInnovations from '../assets/img/network-innovations.png';
import methodArchitecture from '../assets/img/method-architecture.png';

export default {
  name: 'Projects',

  setup() {

    const showPrivateModal = ref(false)

    const handleProjectClick = (project) => {

      if (project.private) {
        showPrivateModal.value = true
        return
      }

      if (project.liveUrl && project.liveUrl !== "#") {
        window.open(project.liveUrl, "_blank")
      }

    }

    const projects = [
      {
        id: 1,
        title: "ATS + CRM",
        description: "A full-featured Applicant Tracking System (ATS) and CRM platform designed to streamline recruitment and client management. Built with the PEVN stack, it includes AI-powered resume parsing, semantic candidate-job matching, interview pipeline tracking, and integrated email/SMS communication tools.",
        image: atsCrm,
        technologies: ["Vue.js", "Node.js", "Postgre", "Express.js", "OpenAi", "Vite", "Tailwind"],
        private: true
      },
      {
        id: 2,
        title: "YouLink",
        description: "YouLink Store is an eCommerce platform designed to streamline online selling through a clean user experience and efficient product management system. It enables businesses to manage inventory, process orders, and handle customer interactions with reliability and scalability in mind.",
        image: youlink,
        technologies: [
          "Magento 2",
          "PHP",
          "MariaDB",
          "HTML5",
          "CSS3",
          "LESS",
          "JavaScript",
          "jQuery",
          "Apache",
          "Composer",
          "Git"
        ],
        liveUrl: "https://youlink.store/",
        private: false
      },
      {
        id: 3,
        title: "Ai Health",
        description: "AiHealth is an AI-powered health inquiry system built to automate and structure medical-related question handling. The platform integrates intelligent response processing, backend logic management, and optimized performance architecture to deliver reliable and scalable digital health assistance.",
        image: aihealth,
        technologies: ["Vue.js", "Node.js", "MongoDB", "Express.js", "OpenAi", "Vite", "Tailwind", "Langchain"],
        private: true
      },
      {
        id: 4,
        title: "PulsePlay",
        description: "PulsePlay is a futuristic product showcase website designed to highlight a next-generation gaming controller through immersive visuals and interactive design. The platform focuses on delivering a dynamic user experience with smooth animations, responsive layouts, and engaging product presentation that emphasizes precision, ergonomics, and customization features.",
        image: pulseplay,
        technologies: ["Webflow", "Lottie Animations", "JavaScript", "jQuery", "CSS3"],
        liveUrl: "https://cartier-design.webflow.io/",
        private: false
      },
      {
        id: 5,
        title: "I'm Insured ",
        description: "I'm Insured is an insurance comparison platform designed to help users easily explore and compare a wide range of insurance products. The platform combines smart online comparison tools with expert adviser support, allowing users to find suitable coverage for life insurance, vehicles, homes, travel, and more. Built to simplify complex insurance decisions, the system focuses on clear information, efficient quote comparisons, and a user-friendly experience.",
        image: iminsured,
        technologies: ["WordPress", "WPBakery", "Salient Theme", "JavaScript", "jQuery", "CSS3"],
        liveUrl: "https://im-insured.co.uk/",
        private: false
      },
      {
        id: 6,
        title: "OMGroup",
        description: "Online Marketing Group (OMGroup) is a digital marketing agency that specializes in performance-driven online marketing strategies. The company helps businesses grow by combining tools such as Google Ads, social media marketing, landing pages, and marketing funnels to generate measurable results and new customers. With a focus on data-driven campaigns and targeted advertising, OMGroup delivers predictable and scalable marketing solutions tailored to each client’s audience and business goals.",
        image: omg,
        technologies: ["WordPress", "Elementor", "CSS3", "JavaScript", "jQuery", "Google Analytics", "SEO Optimization", "Google Ads Integration", "Lottie Animation"],
        liveUrl: "https://online-marketing-group.ch/",
        private: false
      },
      {
        id: 7,
        title: "Network Innovations",
        description: "Network Innovations is a trusted IT service provider that helps businesses build secure, reliable, and customized technology environments. With over 20 years of experience, the company focuses on delivering security-first IT solutions that protect critical data and ensure regulatory compliance. They specialize in supporting industries such as healthcare, finance, and legal, where security and reliability are essential. By providing proactive IT support and strategic technology solutions, Network Innovations helps businesses minimize downtime and focus on growth.",
        image: networkInnovations,
        technologies: ["WordPress", "PHP", "Elementor", "HTML5", "CSS3", "JavaScript", "jQuery", "WP Engine"],
        liveUrl: "https://networkinnostg.wpenginepowered.com/",
        private: false
      },
      {
        id: 8,
        title: "Method Architecture",
        description: "Method Architecture is a full-service architecture and interior design firm that delivers client-focused design solutions across various commercial sectors, including industrial, manufacturing, breweries, and retail. The firm combines the expertise of a large architectural practice with the personalized attention of a boutique studio, ensuring each project receives dedicated support from concept to construction. With an ego-free and collaborative approach, Method Architecture focuses on creating innovative, practical, and community-centered designs that meet the unique needs of its clients.",
        image: methodArchitecture,
        technologies: ["WordPress", "Elementor", "JavaScript ", "jQuery", "HTML5 ", "CSS3", "Yoast SEO", "JetEngine", "JetElements", "Swiper.js"],
        liveUrl: "https://methodarchitecture.com/",
        private: false
      }
    ]

    return {
      projects,
      showPrivateModal,
      handleProjectClick
    }
  }
}
</script>