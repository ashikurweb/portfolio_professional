<template>
    <section ref="heroRef" id="home" class="relative min-h-screen flex items-center pt-20 overflow-hidden bg-[#0A0F1E]">
        <!-- Animated Glow Background -->
        <div class="absolute inset-0 pointer-events-none">
            <div class="glow-1 absolute top-[-10%] left-[-10%] w-[50%] h-[50%] bg-primary/10 rounded-full blur-[120px]">
            </div>
            <div
                class="glow-2 absolute bottom-[-10%] right-[-10%] w-[50%] h-[50%] bg-secondary/5 rounded-full blur-[120px]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10">
            <div class="flex flex-col lg:flex-row items-center justify-between gap-16">
                <div class="flex-1 text-center lg:text-left">
                    <div
                        class="hero-badge inline-flex items-center gap-3 px-5 py-2 rounded-full bg-white/5 border border-white/10 text-primary text-sm font-bold mb-8 opacity-0">
                        <span class="flex h-2 w-2 rounded-full bg-primary animate-pulse"></span>
                        Elevating Digital Experiences
                    </div>

                    <h1 class="hero-title text-6xl md:text-8xl font-black leading-[0.9] mb-8 tracking-tighter">
                        <div class="overflow-hidden"><span class="block line-1">DESIGN</span></div>
                        <div class="overflow-hidden"><span class="block line-2 text-primary italic">THINKING</span>
                        </div>
                        <div class="overflow-hidden"><span class="block line-3">SOLUTIONS</span></div>
                    </h1>

                    <p class="hero-desc text-xl text-gray-400 mb-12 max-w-xl leading-relaxed mx-auto lg:mx-0 opacity-0">
                        I am Alex Morgan, a creative developer pushing the boundaries of what's possible in the modern
                        web.
                    </p>

                    <div class="hero-btns flex flex-wrap items-center justify-center lg:justify-start gap-6 opacity-0">
                        <button
                            class="group relative px-10 py-5 bg-primary text-dark font-black rounded-2xl overflow-hidden transition-all hover:scale-105">
                            <span class="relative z-10">START A PROJECT</span>
                            <div
                                class="absolute inset-0 bg-white translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                            </div>
                        </button>
                        <button
                            class="group px-10 py-5 border border-white/20 text-white font-bold rounded-2xl hover:bg-white/5 transition-all">
                            VIEW WORK
                        </button>
                    </div>
                </div>

                <div class="hero-image-container flex-1 relative opacity-0">
                    <div class="relative w-full max-w-[550px] mx-auto p-4">
                        <!-- Floating Decorative Elements -->
                        <div
                            class="float-item-1 absolute -top-10 -right-10 w-32 h-32 bg-secondary/20 rounded-full blur-2xl">
                        </div>
                        <div
                            class="float-item-2 absolute -bottom-10 -left-10 w-40 h-40 bg-primary/20 rounded-full blur-2xl">
                        </div>

                        <div
                            class="image-wrapper relative aspect-[4/5] rounded-[3rem] overflow-hidden border border-white/10 bg-[#121829] shadow-[0_0_50px_rgba(0,0,0,0.5)]">
                            <img src="/assets/hero.png" alt="Alex Morgan"
                                class="hero-img w-full h-full object-cover grayscale brightness-75 hover:grayscale-0 hover:brightness-100 transition-all duration-700 cursor-pointer" />

                            <!-- Real-time Status Card -->
                            <div
                                class="status-card absolute bottom-8 left-8 right-8 bg-black/40 backdrop-blur-xl border border-white/10 p-6 rounded-[2rem]">
                                <div class="flex items-center justify-between">
                                    <div>
                                        <p class="text-[10px] uppercase tracking-widest text-gray-400 mb-1">Ashikur
                                            Rahman</p>
                                        <h4 class="text-lg font-bold">Junior Software Developer</h4>
                                    </div>
                                    <div
                                        class="w-12 h-12 bg-primary rounded-full flex items-center justify-center text-dark">
                                        <Terminal class="w-6 h-6" />
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Scroll Indicator -->
        <div
            class="hero-scroll-down absolute bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-4 opacity-0">
            <div class="w-[2px] h-12 bg-gradient-to-b from-primary to-transparent"></div>
            <span class="text-[10px] uppercase tracking-[0.3em] font-bold">Scroll</span>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { Terminal } from 'lucide-vue-next'
import gsap from 'gsap'

const heroRef = ref(null)

onMounted(() => {
    const ctx = gsap.context(() => {
        const tl = gsap.timeline({ defaults: { ease: 'power4.out', duration: 1.2 } })

        tl.to('.hero-badge', { opacity: 1, y: 0, duration: 1 })
            .from('.line-1, .line-2, .line-3', {
                y: 150,
                skewY: 10,
                stagger: 0.1,
                duration: 1.5,
            }, '-=0.8')
            .to('.hero-desc', { opacity: 1, y: 0, duration: 1 }, '-=1')
            .to('.hero-btns', { opacity: 1, y: 0, duration: 1 }, '-=1')
            .to('.hero-image-container', { opacity: 1, x: 0, scale: 1, duration: 1.5 }, '-=1.2')
            .to('.hero-scroll-down', { opacity: 0.4, y: 0, duration: 1 }, '-=0.5')

        // Floating animation for decorative elements
        gsap.to('.float-item-1', {
            y: 40,
            duration: 3,
            repeat: -1,
            yoyo: true,
            ease: 'sine.inOut'
        })
        gsap.to('.float-item-2', {
            y: -40,
            duration: 4,
            repeat: -1,
            yoyo: true,
            ease: 'sine.inOut',
            delay: 0.5
        })

        // Mouse movement parallax effect for hero image
        if (heroRef.value) {
            heroRef.value.addEventListener('mousemove', (e) => {
                const { clientX, clientY } = e
                const xPos = (clientX / window.innerWidth - 0.5) * 40
                const yPos = (clientY / window.innerHeight - 0.5) * 40

                gsap.to('.image-wrapper', {
                    x: xPos,
                    y: yPos,
                    duration: 2,
                    ease: 'power2.out'
                })

                gsap.to('.glow-1', {
                    x: xPos * 1.5,
                    y: yPos * 1.5,
                    duration: 3,
                    ease: 'power2.out'
                })
            })
        }
    }, heroRef.value)
})
</script>

<style scoped>
.hero-title {
    text-shadow: 20px 20px 0 rgba(255, 255, 255, 0.02);
}
</style>
