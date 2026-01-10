<script setup>
import Preloader from './components/Preloader.vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Projects from './components/Projects.vue'
import Skills from './components/Skills.vue'
import Testimonials from './components/Testimonials.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <Preloader />
  <div class="min-h-screen bg-[#0A0F1E] text-white">
    <Navbar />
    <main>
      <Hero />
      <About />
      <Projects />
      <Skills />
      <Testimonials />
      <Contact />
    </main>
    <Footer />
  </div>
</template>
