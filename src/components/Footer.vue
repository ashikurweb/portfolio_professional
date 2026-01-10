<script setup>
import { onMounted, ref, markRaw } from 'vue'
import Logo from './Logo.vue'
import { Github, Twitter, Linkedin, Instagram } from 'lucide-vue-next'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const footerRef = ref(null)

const links = [
    { name: 'Home', href: '#' },
    { name: 'About', href: '#about' },
    { name: 'Projects', href: '#projects' },
    { name: 'Skills', href: '#skills' },
    { name: 'Contact', href: '#contact' },
]

// Using markRaw to prevent Vue from making icons reactive
const socials = [
    { name: 'Github', href: '#', icon: markRaw(Github) },
    { name: 'Twitter', href: '#', icon: markRaw(Twitter) },
    { name: 'Linkedin', href: '#', icon: markRaw(Linkedin) },
    { name: 'Instagram', href: '#', icon: markRaw(Instagram) },
]

onMounted(() => {
    const ctx = gsap.context(() => {
        const tl = gsap.timeline({
            scrollTrigger: {
                trigger: footerRef.value,
                start: "top 85%",
                toggleActions: "play none none reverse"
            }
        })

        // Initial States for Modern Reveal
        gsap.set([".footer-bg", ".text-reveal", ".social-card", ".footer-line"], { opacity: 0 })
        gsap.set(".text-reveal", { y: 40 })
        gsap.set([".kinetic-title", ".kinetic-subtitle"], { y: "120%", opacity: 0, rotate: 3 })

        tl.to(".footer-bg", {
            opacity: 1,
            duration: 1.5,
            ease: "power2.out"
        })
            .to(".kinetic-title", {
                y: 0,
                opacity: 1,
                rotate: 0,
                duration: 1.2,
                ease: "expo.out"
            }, "-=1")
            .to(".kinetic-subtitle", {
                y: 0,
                opacity: 1,
                rotate: 0,
                duration: 1,
                ease: "power3.out"
            }, "-=0.8")
            .to(".text-reveal", {
                y: 0,
                opacity: 1,
                duration: 1,
                stagger: 0.1,
                ease: "expo.out"
            }, "-=1")
            .to(".footer-line", {
                scaleX: 1,
                opacity: 1,
                duration: 1.2,
                ease: "power2.inOut"
            }, "-=1")
            .to(".social-card", {
                scale: 1,
                opacity: 1,
                duration: 0.8,
                stagger: 0.08,
                ease: "back.out(1.7)"
            }, "-=1")
    }, footerRef.value)
})
</script>

<template>
    <footer ref="footerRef" class="py-24 bg-[#020408] relative overflow-hidden">
        <!-- Tech Grid Background -->
        <div class="footer-bg absolute inset-0 z-0 pointer-events-none transition-opacity duration-700">
            <div class="absolute inset-0 bg-gradient-to-b from-primary/[0.04] to-transparent"></div>
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff02_1px,transparent_1px),linear-gradient(to_bottom,#ffffff02_1px,transparent_1px)] bg-[size:40px_40px]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-16 mb-20">
                <!-- Brand Column -->
                <div class="space-y-10">
                    <a href="#" class="inline-block group logo-footer text-reveal">
                        <Logo class="group-hover:opacity-80 transition-opacity" />
                    </a>
                    <div class="space-y-6">
                        <div class="overflow-hidden">
                            <h2
                                class="text-gray-400 text-3xl md:text-4xl leading-[1.1] font-light max-w-sm kinetic-title opacity-0">
                                Architecting <br />
                                <span
                                    class="text-white font-black tracking-tight drop-shadow-[0_0_20px_rgba(255,255,255,0.1)]">Digital
                                    Dominance</span>
                            </h2>
                        </div>
                        <div class="overflow-hidden">
                            <p class="text-gray-500 text-sm leading-relaxed max-w-xs kinetic-subtitle opacity-0">
                                Through precision engineering, modern aesthetics, and high-fidelity performance.
                            </p>
                        </div>
                    </div>
                </div>

                <!-- Navigation Column -->
                <div class="nav-col">
                    <h4
                        class="text-white font-black uppercase tracking-[0.4em] text-[10px] mb-10 flex items-center gap-3 text-reveal">
                        <span class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse"></span>
                        Directory
                    </h4>
                    <ul class="space-y-5">
                        <li v-for="link in links" :key="link.name" class="text-reveal">
                            <a :href="link.href"
                                class="text-gray-500 hover:text-white transition-all duration-300 flex items-center gap-4 group text-xs font-bold uppercase tracking-widest">
                                <span class="w-0 h-[1px] bg-primary transition-all duration-500 group-hover:w-6"></span>
                                {{ link.name }}
                            </a>
                        </li>
                    </ul>
                </div>

                <!-- Connect Column -->
                <div class="connect-col">
                    <h4
                        class="text-white font-black uppercase tracking-[0.4em] text-[10px] mb-10 flex items-center gap-3 text-reveal">
                        <span class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse"></span>
                        Network
                    </h4>
                    <div class="grid grid-cols-2 gap-4">
                        <a v-for="social in socials" :key="social.name" :href="social.href"
                            class="social-card group relative h-16 bg-white/[0.02] border border-white/5 overflow-hidden flex items-center justify-center transition-all duration-500 hover:border-primary/40 hover:bg-white/[0.04]">
                            <div
                                class="absolute inset-0 bg-primary opacity-0 group-hover:opacity-5 transition-opacity duration-500">
                            </div>
                            <div class="relative z-10 flex items-center gap-3">
                                <component :is="social.icon"
                                    class="w-4 h-4 text-gray-400 group-hover:text-primary transition-all duration-500 transform group-hover:scale-110" />
                                <span
                                    class="text-[10px] font-mono font-bold text-gray-500 group-hover:text-white uppercase tracking-widest transition-colors">{{
                                        social.name }}</span>
                            </div>
                        </a>
                    </div>
                </div>
            </div>

            <!-- Bottom Bar -->
            <div class="footer-line w-full h-[1px] bg-white/5 mb-10 origin-left opacity-0"></div>
            <div
                class="flex flex-col md:flex-row justify-center items-center gap-8 text-[9px] font-mono text-gray-700 uppercase tracking-[0.4em] font-bold">
                <p class="text-reveal">&copy; 2026 ASHIKUR RAHMAN. ALL SYSTEMS OPERATIONAL.</p>
            </div>
        </div>
    </footer>
</template>

<style scoped>
.footer-bg {
    transform-origin: center;
}
</style>
