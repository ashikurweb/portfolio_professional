<template>
    <nav ref="navRef" class="fixed top-0 left-0 w-full z-50 overflow-hidden">
        <!-- Main Navbar Content -->
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div ref="containerRef" class="flex justify-between items-center h-24">
                <!-- Logo Section -->
                <div class="flex items-center">
                    <a href="#" class="block transform hover:scale-105 transition-transform duration-300">
                        <Logo />
                    </a>
                </div>

                <!-- Desktop Navigation -->
                <div class="hidden md:flex items-center gap-10">
                    <nav class="flex gap-8">
                        <a v-for="link in navLinks" :key="link.name" :href="link.href"
                            class="text-sm font-semibold text-gray-400 hover:text-primary relative group py-2 transition-colors duration-300">
                            {{ link.name }}
                            <span
                                class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
                        </a>
                    </nav>
                    <button
                        class="bg-primary hover:bg-primary/90 text-dark font-black py-3 px-8 rounded-full transition-all hover:scale-105 active:scale-95 shadow-[0_0_20px_rgba(0,210,123,0.3)] hover:shadow-[0_0_30px_rgba(0,210,123,0.5)]">
                        Hire Me
                    </button>
                </div>

                <!-- Mobile Toggle -->
                <button @click="isMobileMenuOpen = !isMobileMenuOpen"
                    class="md:hidden flex flex-col gap-1.5 p-2 z-50 outline-none" aria-label="Toggle Menu">
                    <span class="w-6 h-0.5 bg-white transition-all duration-300"
                        :class="{ 'rotate-45 translate-y-2': isMobileMenuOpen }"></span>
                    <span class="w-6 h-0.5 bg-white transition-opacity duration-300"
                        :class="{ 'opacity-0': isMobileMenuOpen }"></span>
                    <span class="w-6 h-0.5 bg-white transition-all duration-300"
                        :class="{ '-rotate-45 -translate-y-2': isMobileMenuOpen }"></span>
                </button>
            </div>
        </div>

        <!-- Mobile Menu Overlay -->
        <Transition name="fade">
            <div v-if="isMobileMenuOpen" class="md:hidden fixed inset-0 bg-darker/98 backdrop-blur-2xl z-40">
                <div class="flex flex-col items-center justify-center h-full gap-10">
                    <a v-for="(link, index) in navLinks" :key="link.name" :href="link.href"
                        @click="isMobileMenuOpen = false"
                        class="text-3xl font-black text-white hover:text-primary transition-colors transform hover:scale-110 duration-300">
                        <span class="text-primary/30 mr-2 font-mono text-sm">0{{ index + 1 }}</span>
                        {{ link.name }}
                    </a>
                    <button @click="isMobileMenuOpen = false"
                        class="mt-6 bg-primary text-dark font-black py-5 px-12 rounded-xl text-xl shadow-[0_0_30px_rgba(0,210,123,0.3)]">
                        Hire Me
                    </button>
                </div>
            </div>
        </Transition>
    </nav>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue'
import Logo from './Logo.vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const navRef = ref(null)
const containerRef = ref(null)
const isMobileMenuOpen = ref(false)
const isScrolled = ref(false)

const navLinks = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
    { name: 'Contact', href: '#contact' },
]

// Prevent scroll when mobile menu is open
watch(isMobileMenuOpen, (val) => {
    document.body.style.overflow = val ? 'hidden' : ''
})

onMounted(() => {
    const nav = navRef.value
    const container = containerRef.value

    ScrollTrigger.create({
        start: 'top -20',
        onUpdate: (self) => {
            const scrolled = self.scroll() > 20

            if (scrolled !== isScrolled.value) {
                isScrolled.value = scrolled

                if (scrolled) {
                    gsap.to(nav, {
                        backgroundColor: 'rgba(10, 15, 30, 0.85)',
                        backdropFilter: 'blur(24px)',
                        borderBottom: '1px solid rgba(255, 255, 255, 0.1)',
                        boxShadow: '0 15px 40px -15px rgba(0,0,0,0.8)',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                    gsap.to(container, {
                        height: '75px',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                } else {
                    gsap.to(nav, {
                        backgroundColor: 'rgba(10, 15, 30, 0)',
                        backdropFilter: 'blur(0px)',
                        borderBottom: '1px solid rgba(255, 255, 255, 0)',
                        boxShadow: 'none',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                    gsap.to(container, {
                        height: '96px',
                        duration: 0.4,
                        ease: 'expo.out'
                    })
                }
            }
        }
    })
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.4s ease, transform 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>
