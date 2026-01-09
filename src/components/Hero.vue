<template>
    <section ref="heroRef" id="home"
        class="relative min-h-screen flex items-center justify-center overflow-hidden bg-[#020408]">
        <!-- Premium Mesh Gradient Background -->
        <div class="absolute inset-0 pointer-events-none overflow-hidden">
            <!-- Geometric Tech Grid -->
            <div class="absolute inset-0 opacity-[0.03]"
                style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); background-size: 40px 40px;">
            </div>

            <!-- Static Mesh Glows -->
            <div class="glow-1 absolute top-[-20%] left-[-10%] w-[60%] h-[60%] bg-primary/20 rounded-full blur-[140px]">
            </div>
            <div
                class="glow-2 absolute bottom-[-20%] right-[-10%] w-[60%] h-[60%] bg-secondary/10 rounded-full blur-[140px]">
            </div>
            <div
                class="glow-3 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[40%] h-[40%] bg-blue-500/5 rounded-full blur-[120px]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10 py-20">
            <div class="flex flex-col lg:flex-row items-center gap-20">
                <div class="flex-1 space-y-10 min-w-[50%]">
                    <div class="overflow-hidden">
                    </div>

                    <div class="space-y-4">
                        <h1
                            class="text-4xl sm:text-6xl md:text-[7.5rem] font-black tracking-[-0.04em] leading-[0.85] text-white">
                            <div class="overflow-hidden h-[1em] flex items-center"><span class="block title-word"
                                    ref="word1Ref"></span>
                            </div>
                            <div class="overflow-hidden h-[1em] flex items-center">
                                <span class="block title-word-outline text-transparent"
                                    style="-webkit-text-stroke: 1px rgba(255,255,255,0.2)" ref="word2Ref"></span>
                            </div>
                            <div class="overflow-hidden h-[1em] flex items-center text-primary"><span
                                    class="block title-word" ref="word3Ref"></span></div>
                        </h1>
                    </div>

                    <div
                        class="flex flex-col sm:flex-row items-start sm:items-center gap-12 opacity-0 hero-meta translate-y-10">
                        <p class="text-white/30 text-base sm:text-lg max-w-xs leading-relaxed font-medium">
                            Architecting <span class="text-white/60">Digital Ecosystems</span> with a focus on
                            high-fidelity performance.
                        </p>
                        <div class="h-12 w-[1px] bg-white/10 hidden sm:block"></div>
                        <div class="flex flex-col">
                            <span class="text-primary text-xl sm:text-2xl font-black italic">2026</span>
                            <span class="text-[10px] text-white/20 uppercase tracking-[0.4em] font-bold">Edition</span>
                        </div>
                    </div>

                    <div class="flex items-center gap-6 opacity-0 hero-btns-modern translate-y-10">
                        <button
                            class="group relative px-6 sm:px-10 py-3 sm:py-4 bg-primary rounded-lg overflow-hidden transition-all hover:shadow-[0_0_30px_-5px_#00D27B]">
                            <span class="relative z-10 text-black font-black text-sm italic tracking-widest">INITIALIZE
                                PROJECT</span>
                            <div
                                class="absolute inset-0 bg-white -translate-x-full group-hover:translate-x-0 transition-transform duration-500">
                            </div>
                        </button>
                        <button
                            class="px-5 sm:px-8 py-3 sm:py-4 text-white/40 hover:text-white font-bold transition-all text-sm tracking-widest border-b border-white/0 hover:border-white/20">
                            // VIEW_ARCHIVE
                        </button>
                    </div>
                </div>

                <div class="flex-1 relative hero-visual opacity-0 translate-x-20 flex-shrink-0">
                    <div class="relative group max-w-[550px] mx-auto lg:ml-auto select-none">
                        <!-- Modern Glow Aura -->
                        <div
                            class="absolute inset-0 bg-primary/10 blur-[100px] rounded-full scale-110 group-hover:bg-primary/20 transition-all duration-1000">
                        </div>

                        <!-- Main Organic Frame (The "Modern Shaper") -->
                        <div class="relative z-10 aspect-square p-4">
                            <!-- Squircle Masked Image with Continuous Animation -->
                            <div
                                class="relative w-full h-full overflow-hidden modern-organic-animation group-hover:scale-[1.02] transition-transform duration-700 shadow-2xl">
                                <!-- Inner Border Glow -->
                                <div
                                    class="absolute inset-0 border-[8px] border-white/5 rounded-inherit z-10 pointer-events-none">
                                </div>

                                <img src="/assets/hero.jpg" alt="Ashikur"
                                    class="w-full h-full object-cover grayscale brightness-90 group-hover:grayscale-0 group-hover:brightness-100 group-hover:scale-110 transition-all duration-1000 ease-out" />

                                <!-- Sleek Gradient Overlay -->
                                <div
                                    class="absolute inset-0 bg-gradient-to-t from-darker via-transparent to-transparent opacity-60">
                                </div>
                            </div>

                            <!-- Decorative Orbit Ring -->
                            <div
                                class="absolute inset-0 border border-white/10 rounded-full scale-125 animate-[spin_20s_linear_infinite] opacity-30">
                            </div>
                        </div>

                        <!-- Abstract Cursor Hub -->
                        <div ref="cursorFollower"
                            class="absolute w-20 h-20 bg-primary/10 backdrop-blur-md rounded-full -translate-x-1/2 -translate-y-1/2 pointer-events-none opacity-0 border border-primary/20 z-50 flex items-center justify-center">
                            <div class="w-2 h-2 bg-primary rounded-full"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Global Coordinate Data -->
        <div class="absolute bottom-10 right-10 flex gap-10 opacity-20 hidden md:flex">
            <div class="flex flex-col text-[10px] text-white font-mono uppercase tracking-widest">
                <span>LAT: 23.8103</span>
                <span>LNG: 90.4125</span>
            </div>
            <div class="flex flex-col text-[10px] text-white font-mono uppercase tracking-widest">
                <span>CPU: 0.002s</span>
                <span>RND: 73DC94C</span>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { Terminal } from 'lucide-vue-next'
import gsap from 'gsap'
import { TextPlugin } from 'gsap/TextPlugin'

gsap.registerPlugin(TextPlugin)

const heroRef = ref(null)
const word1Ref = ref(null)
const word2Ref = ref(null)
const word3Ref = ref(null)
const cursorFollower = ref(null)

onMounted(() => {
    const ctx = gsap.context(() => {
        const tl = gsap.timeline({ defaults: { ease: 'power4.out', duration: 1.5 } })

        // Initial Reveal
        tl.to('.hero-badge-modern', { opacity: 1, y: 0, duration: 1 })
            .to('.hero-visual', { opacity: 1, x: 0, duration: 2 }, '-=0.5')
            .to('.hero-meta', { opacity: 1, y: 0 }, '-=1.5')
            .to('.hero-btns-modern', { opacity: 1, y: 0 }, '-=1.3')

        // Professional Typing Sequence (Smooth & Looping)
        const typeTl = gsap.timeline({ repeat: -1 })

        typeTl
            .to(word1Ref.value, { text: "DEVELOPMENT", duration: 0.6, ease: "none" })
            .to(word2Ref.value, { text: "THINKING", duration: 0.8, ease: "none" })
            .to(word3Ref.value, { text: "SOLUTIONS", duration: 0.8, ease: "none" })
            .to({}, { duration: 3 })
            .to([word1Ref.value, word2Ref.value, word3Ref.value], { text: "", duration: 0.6, ease: "power2.inOut", stagger: 0.1 })
            .to({}, { duration: 0.5 })

        // Floating Motion
        gsap.to('.hero-visual', {
            y: -20,
            duration: 4,
            repeat: -1,
            yoyo: true,
            ease: 'sine.inOut'
        })

        // Interactive Tracking
        if (heroRef.value) {
            heroRef.value.addEventListener('mousemove', (e) => {
                const { clientX, clientY } = e
                const rect = heroRef.value.getBoundingClientRect()
                const x = clientX - rect.left
                const y = clientY - rect.top

                gsap.to(cursorFollower.value, {
                    x, y,
                    opacity: 1,
                    duration: 0.6,
                    ease: 'power2.out'
                })

                // Subtle Parallax
                gsap.to('.main-frame', {
                    rotateY: (clientX / window.innerWidth - 0.5) * 10,
                    rotateX: (clientY / window.innerHeight - 0.5) * -10,
                    duration: 1,
                    ease: 'power2.out'
                })
            })

            heroRef.value.addEventListener('mouseleave', () => {
                gsap.to(cursorFollower.value, { opacity: 0, duration: 0.5 })
            })
        }
    }, heroRef.value)
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@900&display=swap');

.modern-organic-animation {
    animation: morphing 10s ease-in-out infinite;
    transition: all 0.8s ease;
}

@keyframes morphing {
    0% {
        border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    }

    25% {
        border-radius: 58% 42% 75% 25% / 76% 46% 54% 24%;
    }

    50% {
        border-radius: 50% 50% 33% 67% / 55% 27% 73% 45%;
    }

    75% {
        border-radius: 33% 67% 58% 42% / 63% 68% 32% 37%;
    }

    100% {
        border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    }
}

.title-word {
    font-family: 'Big Shoulders Display', sans-serif;
}

.title-word-outline {
    -webkit-text-stroke: 1px rgba(255, 255, 255, 0.2);
    color: transparent;
}

.noise-bg {
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3e%3cfilter id='noiseFilter'%3e%3cfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3e%3c/filter%3e%3crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3e%3c/svg%3e");
}
</style>
