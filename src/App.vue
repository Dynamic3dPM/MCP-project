<template>
  <v-app>
    <!-- Navigation with Animation -->
    <v-app-bar
      app
      color="rgba(255,255,255,0.95)"
      elevation="0"
      fixed
      class="nav-blur"
      :class="{ 'nav-scrolled': scrolled }"
    >
      <v-toolbar-title class="text-h5 font-weight-bold primary--text logo-animate">
        <v-icon color="primary" class="mr-2 rotate-icon">mdi-brain</v-icon>
        MCP Protocol
      </v-toolbar-title>
      
      <v-spacer></v-spacer>
      
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn
          v-for="(item, index) in navItems"
          :key="item.id"
          text
          @click="scrollTo(item.id)"
          class="text-capitalize nav-btn"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <v-icon left size="20">{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>

      <!-- Mobile menu -->
      <v-app-bar-nav-icon
        class="hidden-md-and-up pulse-icon"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
    </v-app-bar>

    <!-- Mobile Navigation Drawer with Animation -->
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      class="mobile-drawer"
    >
      <v-list class="pt-8">
        <v-list-item
          v-for="(item, index) in navItems"
          :key="item.title"
          @click="scrollTo(item.id); drawer = false"
          class="mobile-nav-item"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <v-list-item-icon>
            <v-icon color="primary">{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- Main Content -->
    <v-main>
      <!-- Enhanced Hero Section -->
      <v-container fluid class="hero-section pa-0">
        <div class="hero-overlay"></div>
        <v-row no-gutters>
          <v-col cols="12">
            <div class="hero-content text-center white--text py-16">
              <div class="hero-icon-container mb-6">
                <v-icon size="120" class="hero-icon bounce-in">mdi-brain</v-icon>
                <div class="floating-particles">
                  <div class="particle" v-for="n in 6" :key="n"></div>
                </div>
              </div>
              <h1 class="display-2 font-weight-light mb-4 fade-in-up" style="animation-delay: 0.3s">
                Model Content Protocol (MCP)
              </h1>
              <p class="headline font-weight-light fade-in-up" style="animation-delay: 0.6s">
                The Future of AI Integration and Content Management
              </p>
              <v-btn
                large
                color="white"
                class="primary--text mt-6 pulse-btn fade-in-up"
                style="animation-delay: 0.9s"
                @click="scrollTo('what-is-mcp')"
              >
                <v-icon left>mdi-rocket-launch</v-icon>
                Get Started
              </v-btn>
            </div>
          </v-col>
        </v-row>
      </v-container>

      <v-container class="py-12">
        <!-- What is MCP Section -->
        <section id="what-is-mcp" class="mb-16">
          <v-row justify="center">
            <v-col cols="12" md="10">
              <div class="section-header text-center mb-8">
                <v-icon size="64" color="primary" class="mb-4 bounce-icon">mdi-help-circle</v-icon>
                <h2 class="text-h3 primary--text fade-in-title">
                  What is Model Content Protocol?
                </h2>
              </div>
              <v-card elevation="8" class="pa-8 card-hover glass-card">
                <p class="text-body-1 mb-6 fade-in-content">
                  The Model Content Protocol (MCP) is a standardized specification for integrating AI models with external tools and data sources. It enables seamless communication between AI systems and external services, allowing for:
                </p>
                <v-list class="transparent">
                  <v-list-item 
                    v-for="(item, index) in mcpFeatures" 
                    :key="item"
                    class="feature-item"
                    :style="{ animationDelay: `${index * 0.2}s` }"
                  >
                    <v-list-item-icon>
                      <v-icon color="success" class="check-icon">mdi-check-circle</v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <v-list-item-title class="text-body-1">{{ item }}</v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <!-- Architecture Section -->
        <section id="architecture" class="mb-16">
          <v-row justify="center">
            <v-col cols="12" md="10">
              <div class="section-header text-center mb-8">
                <v-icon size="64" color="primary" class="mb-4 rotate-icon">mdi-sitemap</v-icon>
                <h2 class="text-h3 primary--text fade-in-title">
                  Architecture
                </h2>
              </div>
              <v-card elevation="8" class="pa-8 card-hover glass-card">
                <div class="text-center mb-6">
                  <ArchitectureDiagram />
                </div>
                <p class="text-body-1 mb-6 fade-in-content">
                  MCP operates on a layered architecture that includes:
                </p>
                <v-list class="transparent">
                  <v-list-item 
                    v-for="(layer, index) in architectureLayers" 
                    :key="layer.name"
                    class="layer-item"
                    :style="{ animationDelay: `${index * 0.2}s` }"
                  >
                    <v-list-item-icon>
                      <v-icon color="primary" class="layer-icon">mdi-layers</v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <v-list-item-title class="font-weight-medium text-h6">
                        {{ layer.name }}
                      </v-list-item-title>
                      <v-list-item-subtitle class="text-body-1 mt-1">
                        {{ layer.description }}
                      </v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <!-- Use Cases Section -->
        <section id="use-cases" class="mb-16">
          <v-row justify="center">
            <v-col cols="12" md="10">
              <div class="section-header text-center mb-8">
                <v-icon size="64" color="primary" class="mb-4 pulse-icon">mdi-lightbulb</v-icon>
                <h2 class="text-h3 primary--text fade-in-title">
                  Use Cases
                </h2>
              </div>
              <v-row>
                <v-col
                  v-for="(useCase, index) in useCases"
                  :key="useCase.title"
                  cols="12"
                  md="4"
                >
                  <v-card
                    elevation="8"
                    class="pa-6 text-center h-100 use-case-card glass-card"
                    hover
                    :style="{ animationDelay: `${index * 0.2}s` }"
                  >
                    <div class="icon-container mb-4">
                      <v-icon
                        size="80"
                        color="primary"
                        class="use-case-icon"
                      >
                        {{ useCase.icon }}
                      </v-icon>
                    </div>
                    <h3 class="text-h5 mb-4 font-weight-bold">{{ useCase.title }}</h3>
                    <p class="text-body-1">{{ useCase.description }}</p>
                  </v-card>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
        </section>

        <!-- Benefits Section -->
        <section id="benefits" class="mb-16">
          <v-row justify="center">
            <v-col cols="12" md="10">
              <div class="section-header text-center mb-8">
                <v-icon size="64" color="success" class="mb-4 bounce-icon">mdi-star-circle</v-icon>
                <h2 class="text-h3 primary--text fade-in-title">
                  Benefits
                </h2>
              </div>
              <v-card elevation="8" class="pa-8 card-hover glass-card">
                <v-list class="transparent">
                  <v-list-item
                    v-for="(benefit, index) in benefits"
                    :key="benefit.title"
                    class="px-0 benefit-item"
                    :style="{ animationDelay: `${index * 0.15}s` }"
                  >
                    <v-list-item-icon>
                      <v-icon color="success" class="benefit-icon">{{ benefit.icon }}</v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <v-list-item-title class="font-weight-bold text-h6">
                        {{ benefit.title }}
                      </v-list-item-title>
                      <v-list-item-subtitle class="text-body-1 mt-2">
                        {{ benefit.description }}
                      </v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-col>
          </v-row>
        </section>
      </v-container>
    </v-main>

    <!-- Enhanced Footer -->
    <v-footer
      color="primary"
      dark
      padless
      class="footer-gradient"
    >
      <v-col
        class="text-center white--text py-6"
        cols="12"
      >
        <div class="mb-4">
          <v-icon size="32" class="mr-2 pulse-icon">mdi-brain</v-icon>
          <span class="text-h6">MCP Protocol</span>
        </div>
        <p class="mb-2">© 2025 Model Content Protocol Documentation</p>
        <div class="social-icons">
          <v-btn icon color="white" class="mx-1 social-btn">
            <v-icon>mdi-github</v-icon>
          </v-btn>
          <v-btn icon color="white" class="mx-1 social-btn">
            <v-icon>mdi-twitter</v-icon>
          </v-btn>
          <v-btn icon color="white" class="mx-1 social-btn">
            <v-icon>mdi-linkedin</v-icon>
          </v-btn>
        </div>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
import ArchitectureDiagram from './components/ArchitectureDiagram.vue'

export default {
  name: 'App',
  components: {
    ArchitectureDiagram
  },
  data() {
    return {
      drawer: false,
      scrolled: false,
      navItems: [
        { title: 'What is MCP?', id: 'what-is-mcp', icon: 'mdi-help-circle' },
        { title: 'Architecture', id: 'architecture', icon: 'mdi-sitemap' },
        { title: 'Use Cases', id: 'use-cases', icon: 'mdi-lightbulb' },
        { title: 'Benefits', id: 'benefits', icon: 'mdi-star-circle' }
      ],
      mcpFeatures: [
        'Unified data access and manipulation',
        'Standardized resource management',
        'Consistent tool integration',
        'Enhanced AI system capabilities'
      ],
      architectureLayers: [
        {
          name: 'Resource Layer',
          description: 'Manages external resources and data sources'
        },
        {
          name: 'Tool Layer',
          description: 'Handles tool integration and execution'
        },
        {
          name: 'Protocol Layer',
          description: 'Standardizes communication between components'
        }
      ],
      useCases: [
        {
          title: 'Code Development',
          description: 'Integrate AI assistants with development tools and code repositories',
          icon: 'mdi-code-tags'
        },
        {
          title: 'Design Tools',
          description: 'Enable AI-powered design assistance and asset management',
          icon: 'mdi-palette'
        },
        {
          title: 'Search Integration',
          description: 'Enhance search capabilities with AI-powered content understanding',
          icon: 'mdi-magnify'
        }
      ],
      benefits: [
        {
          title: 'Standardization',
          description: 'Consistent integration across different AI systems',
          icon: 'mdi-format-list-checks'
        },
        {
          title: 'Extensibility',
          description: 'Easy to add new tools and resources',
          icon: 'mdi-puzzle'
        },
        {
          title: 'Security',
          description: 'Controlled access to external resources',
          icon: 'mdi-shield-check'
        },
        {
          title: 'Efficiency',
          description: 'Optimized resource utilization',
          icon: 'mdi-speedometer'
        }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
    this.animateOnScroll()
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    scrollTo(elementId) {
      const element = document.getElementById(elementId)
      if (element) {
        element.scrollIntoView({
          behavior: 'smooth',
          block: 'start'
        })
      }
    },
    handleScroll() {
      this.scrolled = window.scrollY > 50
    },
    animateOnScroll() {
      const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -50px 0px'
      }

      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('animate-in')
          }
        })
      }, observerOptions)

      // Observe all animated elements
      this.$nextTick(() => {
        const animatedElements = document.querySelectorAll('.fade-in-title, .fade-in-content, .feature-item, .layer-item, .use-case-card, .benefit-item')
        animatedElements.forEach(el => observer.observe(el))
      })
    }
  }
}
</script>

<style scoped>
/* Navigation Animations */
.nav-blur {
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.nav-scrolled {
  background: rgba(255,255,255,0.98) !important;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1) !important;
}

.logo-animate {
  animation: slideInLeft 0.8s ease-out;
}

.nav-btn {
  animation: slideInDown 0.6s ease-out;
  transition: all 0.3s ease;
}

.nav-btn:hover {
  transform: translateY(-2px);
}

/* Hero Section Animations */
.hero-section {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  position: relative;
  overflow: hidden;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.2);
}

.hero-content {
  position: relative;
  z-index: 2;
  padding: 150px 0 100px 0;
}

.hero-icon-container {
  position: relative;
  display: inline-block;
}

.hero-icon {
  color: white;
  filter: drop-shadow(0 4px 8px rgba(0,0,0,0.3));
}

.floating-particles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: white;
  border-radius: 50%;
  animation: float 3s ease-in-out infinite;
}

.particle:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
.particle:nth-child(2) { top: 20%; right: 10%; animation-delay: 0.5s; }
.particle:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 1s; }
.particle:nth-child(4) { bottom: 10%; right: 20%; animation-delay: 1.5s; }
.particle:nth-child(5) { top: 50%; left: 5%; animation-delay: 2s; }
.particle:nth-child(6) { top: 40%; right: 5%; animation-delay: 2.5s; }

/* Card Enhancements */
.glass-card {
  background: rgba(255,255,255,0.95) !important;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.3);
}

.card-hover {
  transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.card-hover:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0,0,0,0.15) !important;
}

.use-case-card {
  animation: slideInUp 0.8s ease-out;
  transition: all 0.4s ease;
}

.use-case-card:hover {
  transform: translateY(-12px) scale(1.05);
  box-shadow: 0 25px 50px rgba(0,0,0,0.2) !important;
}

.use-case-card:hover .use-case-icon {
  transform: scale(1.2) rotate(360deg);
}

/* Icon Animations */
.bounce-icon {
  animation: bounce 2s ease-in-out infinite;
}

.rotate-icon {
  animation: rotate 4s linear infinite;
}

.pulse-icon {
  animation: pulse 2s ease-in-out infinite;
}

.check-icon {
  animation: checkmark 0.6s ease-out;
}

.layer-icon {
  animation: layerPulse 2s ease-in-out infinite;
}

.use-case-icon {
  transition: all 0.4s ease;
}

.benefit-icon {
  animation: benefitGlow 2s ease-in-out infinite alternate;
}

.pulse-btn {
  animation: buttonPulse 2s ease-in-out infinite;
}

.pulse-btn:hover {
  transform: scale(1.05);
}

/* Footer Enhancements */
.footer-gradient {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) !important;
}

.social-btn {
  transition: all 0.3s ease;
}

.social-btn:hover {
  transform: translateY(-3px) scale(1.1);
}

/* Mobile Drawer */
.mobile-drawer {
  background: linear-gradient(180deg, #f8f9fa 0%, #e9ecef 100%);
}

.mobile-nav-item {
  animation: slideInRight 0.6s ease-out;
}

/* Scroll Animations */
.fade-in-up {
  animation: fadeInUp 1s ease-out;
}

.fade-in-title,
.fade-in-content,
.feature-item,
.layer-item,
.benefit-item {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.6s ease-out;
}

.animate-in {
  opacity: 1 !important;
  transform: translateY(0) !important;
}

/* Keyframe Animations */
@keyframes slideInLeft {
  from { transform: translateX(-100px); opacity: 0; }
  to { transform: translateX(0); opacity: 1; }
}

@keyframes slideInDown {
  from { transform: translateY(-50px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

@keyframes slideInUp {
  from { transform: translateY(50px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

@keyframes slideInRight {
  from { transform: translateX(100px); opacity: 0; }
  to { transform: translateX(0); opacity: 1; }
}

@keyframes fadeInUp {
  from { transform: translateY(30px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-10px); }
  60% { transform: translateY(-5px); }
}

@keyframes bounceIn {
  0% { transform: scale(0.3); opacity: 0; }
  50% { transform: scale(1.05); }
  70% { transform: scale(0.9); }
  100% { transform: scale(1); opacity: 1; }
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  33% { transform: translateY(-10px) rotate(120deg); }
  66% { transform: translateY(5px) rotate(240deg); }
}

@keyframes checkmark {
  0% { transform: scale(0) rotate(0deg); }
  50% { transform: scale(1.2) rotate(180deg); }
  100% { transform: scale(1) rotate(360deg); }
}

@keyframes layerPulse {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50% { transform: scale(1.1); opacity: 1; }
}

@keyframes benefitGlow {
  from { filter: brightness(1); }
  to { filter: brightness(1.3); }
}

@keyframes buttonPulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(25, 118, 210, 0.4); }
  50% { box-shadow: 0 0 0 20px rgba(25, 118, 210, 0); }
}

/* Responsive Adjustments */
@media (max-width: 960px) {
  .hero-content {
    padding: 120px 20px 80px 20px;
  }
  
  .hero-icon {
    font-size: 80px !important;
  }
  
  .display-2 {
    font-size: 2.5rem !important;
  }
}

@media (max-width: 600px) {
  .hero-icon {
    font-size: 60px !important;
  }
  
  .display-2 {
    font-size: 2rem !important;
  }
  
  .section-header .v-icon {
    font-size: 48px !important;
  }
}

/* Transparency for lists */
.transparent {
  background: transparent !important;
}

.section-header {
  animation: fadeInUp 0.8s ease-out;
}

.icon-container {
  position: relative;
  overflow: hidden;
}

.h-100 {
  height: 100%;
}
</style>