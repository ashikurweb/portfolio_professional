<template>
    <nav ref="navRef" class="fixed top-0 left-0 w-full z-50 transition-all duration-500">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <div class="flex items-center">
                    <a href="#">
                        <Logo />
                    </a>
                </div>

                <div class="hidden md:flex items-center gap-8">
                    <a v-for="link in navLinks" :key="link.name" :href="link.href"
                        class="text-sm font-medium text-gray-400 hover:text-primary transition-colors">
                        {{ link.name }}
                    </a>
                    <button
                        class="bg-primary hover:bg-primary/90 text-dark font-bold py-2.5 px-6 rounded-full transition-all hover:scale-105 active:scale-95">
                        Hire Me
                    </button>
                </div>

                <!-- Mobile button would go here -->
            </div>
        </div>
    </nav>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Logo from './Logo.vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const navRef = ref(null)

const navLinks = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
    { name: 'Contact', href: '#contact' },
]

onMounted(() => {
    ScrollTrigger.create({
        start: 'top -50',
        onUpdate: (self) => {
            if (self.direction === 1) { // Scrolling down
                gsap.to(navRef.value, {
                    backgroundColor: 'rgba(10, 15, 30, 0.9)',
                    backdropFilter: 'blur(16px)',
                    borderBottom: '1px solid rgba(255, 255, 255, 0.05)',
                    height: '70px',
                    duration: 0.4,
                    ease: 'power2.out'
                })
            } else if (self.scroll() < 50) { // Near top
                gsap.to(navRef.value, {
                    backgroundColor: 'transparent',
                    backdropFilter: 'blur(0px)',
                    borderBottom: '1px solid rgba(255, 255, 255, 0)',
                    height: '80px',
                    duration: 0.4,
                    ease: 'power2.out'
                })
            }
        }
    })
})
</script>
