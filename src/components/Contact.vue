<template>
    <section id="contact" class="py-32 bg-[#020408] relative overflow-hidden" ref="contactRef">
        <!-- Technical Background Grid -->
        <div class="absolute inset-0 z-0 pointer-events-none">
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_0%,#000_70%,transparent_100%)]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <!-- Massive Header -->
            <div class="mb-24 contact-header">
                <div class="flex items-center gap-4 mb-6 reveal-meta opacity-0">
                    <span class="w-12 h-[1px] bg-primary/40"></span>
                    <span
                        class="text-[10px] font-mono font-black text-primary tracking-[0.6em] uppercase animate-pulse">
                        // INITIATE_PROTOCOL
                    </span>
                </div>
                <h2
                    class="text-5xl sm:text-7xl md:text-[8rem] font-black italic uppercase leading-[0.85] tracking-tighter text-white mb-8 perspective-[1000px]">
                    <div class="overflow-hidden"><span class="block reveal-text-contact origin-bottom">LET'S</span>
                    </div>
                    <div class="overflow-hidden"><span class="block text-transparent reveal-text-contact origin-bottom"
                            style="-webkit-text-stroke: 1px rgba(255,255,255,0.2);">BUILD</span></div>
                    <div class="overflow-hidden"><span class="block text-primary reveal-text-contact origin-bottom">THE
                            FUTURE</span></div>
                </h2>
            </div>

            <div class="grid lg:grid-cols-2 gap-20 contact-content">
                <!-- Left: Contact Methods -->
                <div class="space-y-12">
                    <p class="text-xl text-gray-400 leading-relaxed font-light reveal-fade opacity-0">
                        Ready to transform concepts into digital reality? <br />
                        Signal status: <span class="text-green-400 font-mono text-sm tracking-widest uppercase">[ ONLINE
                            ]</span>
                    </p>

                    <div class="grid gap-6">
                        <div v-for="(info, index) in contactInfo" :key="index"
                            class="group relative overflow-hidden border border-white/5 bg-white/[0.02] hover:bg-white/[0.05] p-8 transition-all duration-500 hover:border-primary/30 contact-card opacity-0 translate-y-10">

                            <div
                                class="absolute inset-0 bg-gradient-to-r from-primary/0 via-primary/5 to-primary/0 translate-x-[-100%] group-hover:translate-x-[100%] transition-transform duration-1000">
                            </div>

                            <div class="relative z-10 flex items-center gap-6">
                                <div
                                    class="w-12 h-12 rounded-full border border-primary/20 bg-primary/5 flex items-center justify-center text-primary group-hover:scale-110 group-hover:bg-primary group-hover:text-black transition-all duration-500">
                                    <component :is="info.icon" class="w-5 h-5" />
                                </div>
                                <div>
                                    <div class="text-[10px] uppercase font-mono text-gray-500 tracking-[0.2em] mb-1">{{
                                        info.label }}</div>
                                    <div
                                        class="text-xl font-bold text-white tracking-tight group-hover:text-primary transition-colors">
                                        {{ info.value }}</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Right: High-Tech Form -->
                <div class="relative">
                    <div
                        class="absolute -inset-1 bg-gradient-to-b from-primary/20 to-transparent rounded-[2rem] blur-xl opacity-20">
                    </div>
                    <form @submit.prevent
                        class="relative bg-black/40 backdrop-blur-xl border border-white/10 rounded-[2rem] p-8 md:p-12 space-y-8">
                        <div class="grid md:grid-cols-2 gap-8">
                            <div class="group relative form-item opacity-0 translate-y-4">
                                <label
                                    class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Coordinates
                                    [Name]</label>
                                <input type="text"
                                    class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                    placeholder="John Doe" />
                            </div>
                            <div class="group relative form-item opacity-0 translate-y-4">
                                <label
                                    class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Communication
                                    Link [Email]</label>
                                <input type="email"
                                    class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                    placeholder="john@example.com" />
                            </div>
                        </div>

                        <div class="group relative form-item opacity-0 translate-y-4">
                            <label
                                class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">System
                                Header [Subject]</label>
                            <input type="text"
                                class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg"
                                placeholder="Project Proposal" />
                        </div>

                        <div class="group relative form-item opacity-0 translate-y-4">
                            <label
                                class="text-xs font-mono text-gray-500 tracking-wider uppercase mb-2 block group-focus-within:text-primary transition-colors">Data
                                Payload [Message]</label>
                            <textarea rows="4"
                                class="w-full bg-transparent border-b border-white/10 py-3 text-white focus:border-primary focus:outline-none transition-all placeholder:text-white/10 font-light text-lg resize-none"
                                placeholder="Tell me about your project..."></textarea>
                        </div>

                        <button
                            class="w-full group relative px-8 py-5 bg-white text-black font-bold uppercase tracking-widest overflow-hidden transition-all hover:bg-primary form-item opacity-0 translate-y-4">
                            <span class="relative z-10 flex items-center justify-center gap-3">
                                Initialize Transmission
                                <svg xmlns="http://www.w3.org/2000/svg"
                                    class="w-5 h-5 transition-transform group-hover:translate-x-1" fill="none"
                                    viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M14 5l7 7m0 0l-7 7m7-7H3" />
                                </svg>
                            </span>
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { Mail, Phone, MapPin } from 'lucide-vue-next'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
const contactRef = ref(null)

const contactInfo = [
    { label: 'Secure Channel', value: 'hello@alexmorgan.com', icon: Mail },
    { label: 'Voice Link', value: '+1 (555) 000-0000', icon: Phone },
    { label: 'Base Station', value: 'San Francisco, CA', icon: MapPin },
]

onMounted(() => {
    const ctx = gsap.context(() => {

        // 1. Header Text Scrub Animation (Scroll-driven)
        const headerTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.contact-header',
                start: 'top bottom', // Start when header enters view
                end: 'center center', // End when centered
                scrub: 1, // Smooth scrubbing
            }
        })

        headerTl.from('.reveal-text-contact', {
            y: '120%',
            skewY: 10,
            opacity: 0,
            stagger: 0.1,
            duration: 1,
            ease: 'power4.out'
        })
            .from('.reveal-meta', { opacity: 0, duration: 0.5 }, 0)

        // 2. Form & Cards (Auto-play when visible)
        const contentTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.contact-content',
                start: 'top 80%',
                end: 'bottom 10%',
                toggleActions: 'play reverse play reverse'
            }
        })

        // Left Side
        contentTl.to('.reveal-fade', { opacity: 1, y: 0, duration: 0.6 })
            .to('.contact-card', {
                opacity: 1,
                y: 0,
                stagger: 0.1,
                duration: 0.8,
                ease: 'back.out(1.7)'
            }, '-=0.4')

            // Right Side (Form)
            .to('.form-item', {
                opacity: 1,
                y: 0,
                stagger: 0.1,
                duration: 0.8,
                ease: 'power3.out'
            }, '-=0.6')

    }, contactRef.value)
})
</script>
