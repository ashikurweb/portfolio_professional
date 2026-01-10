<template>
    <Transition name="fade">
        <div v-if="!isLoaded" class="preloader-base fixed inset-0 z-[9999] bg-[#020202] overflow-hidden">

            <!-- Luxury Perspective Grid -->
            <div class="absolute inset-0 z-0 perspective-grid opacity-20"></div>

            <!-- Split Exit Panels (Preserved as requested) -->
            <div
                class="split-panel top-panel absolute top-0 left-0 w-full h-1/2 bg-[#050505] border-b border-primary/10">
            </div>
            <div
                class="split-panel bottom-panel absolute bottom-0 left-0 w-full h-1/2 bg-[#050505] border-t border-primary/10">
            </div>

            <!-- Unique Central Architecture -->
            <div class="relative z-10 flex flex-col items-center justify-center h-full">

                <!-- The "Glitch-Pulse" Core -->
                <div class="unique-core-container relative scale-110">

                    <!-- Abstract Floating Orbits -->
                    <div v-for="i in 3" :key="i"
                        class="absolute inset-[-40px] border border-primary/20 rounded-full animate-orbit" :style="{
                            animationDelay: `${i * -2}s`,
                            transform: `rotateX(${60 + i * 10}deg) rotateY(${i * 20}deg)`
                        }">
                    </div>

                    <!-- The Modern Geometric 'A' -->
                    <div class="relative w-32 h-32 flex items-center justify-center">
                        <!-- Glass Hexagon -->
                        <div
                            class="absolute inset-0 bg-white/[0.02] backdrop-blur-xl border border-white/10 rounded-3xl rotate-12 transition-transform duration-1000">
                        </div>

                        <!-- Kinetic SVG Path -->
                        <svg viewBox="0 0 100 100" class="w-16 h-16 relative z-10">
                            <path class="kinetic-path" d="M30 75 L50 25 L70 75 M42 60 L58 60"
                                stroke="var(--color-primary)" stroke-width="8" stroke-linecap="round"
                                stroke-linejoin="round" fill="none" />

                            <!-- Floating Energy Points -->
                            <circle cx="50" cy="25" r="3" fill="var(--color-secondary)"
                                class="animate-ping shadow-[0_0_15px_var(--color-secondary)]" />
                        </svg>
                    </div>
                </div>

                <!-- Luxury Progress Indicator -->
                <div class="mt-24 flex flex-col items-center gap-6">
                    <div class="flex items-center gap-4 text-white/40 font-mono text-[10px] tracking-[0.6em]">
                        <span>SYSTEM</span>
                        <div class="w-16 h-[1px] bg-white/10 relative overflow-hidden">
                            <div class="absolute inset-0 bg-primary animate-scanning-line"></div>
                        </div>
                        <span>SYNC</span>
                    </div>

                    <!-- Oversized Counter Masked -->
                    <div class="relative h-20 overflow-hidden">
                        <h1
                            class="text-8xl font-black italic tracking-tighter text-white opacity-10 leading-none counter-reveal">
                            {{ Math.floor(progress) }}
                        </h1>
                    </div>

                    <!-- Slim Status Line -->
                    <div class="w-48 h-1 bg-white/[0.03] rounded-full overflow-hidden">
                        <div class="h-full bg-gradient-to-r from-primary to-blue-500 transition-all duration-300 shadow-[0_0_20px_rgba(34,197,94,0.3)]"
                            :style="{ width: `${progress}%` }"></div>
                    </div>
                </div>
            </div>

            <!-- Bottom Meta Strips -->
            <div class="absolute bottom-10 left-0 w-full px-10 flex justify-between items-end opacity-0 footer-meta">
                <div class="flex flex-col gap-1">
                    <span class="text-[8px] text-gray-700 tracking-[0.4em] font-mono uppercase">EST_ARCH_2024</span>
                    <span class="text-[9px] text-primary/40 font-bold uppercase tracking-widest">Protocol.Alpha</span>
                </div>
                <div class="text-[10px] text-gray-700 font-mono tracking-[0.2em]">
                    ASHIKUR_PORTFOLIO / V3.0
                </div>
            </div>
        </div>
    </Transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

const isLoaded = ref(false)
const progress = ref(0)

onMounted(() => {
    document.body.style.overflow = 'hidden'

    const tl = gsap.timeline({
        onComplete: () => {
            setTimeout(exitSequence, 500)
        }
    })

    // Powerful Entrance
    tl.to('.unique-core-container', {
        y: 0,
        opacity: 1,
        duration: 1.5,
        ease: "expo.out"
    })
        .from('.kinetic-path', {
            strokeDasharray: 200,
            strokeDashoffset: 200,
            duration: 2,
            ease: "power3.inOut"
        }, "-=1")
        .to('.counter-reveal', {
            y: 0,
            opacity: 0.1,
            duration: 1,
            ease: "power4.out"
        }, "-=1.2")
        .to('.footer-meta', {
            opacity: 1,
            duration: 1,
            ease: "power2.out"
        }, "-=0.8")

    // Progress Sync
    gsap.to(progress, {
        value: 100,
        duration: 3.5,
        ease: "power2.inOut"
    })
})

const exitSequence = () => {
    const tl = gsap.timeline({
        onComplete: () => {
            isLoaded.value = true
            document.body.style.overflow = ''
        }
    })

    tl.to('.unique-core-container, .mt-24, .footer-meta', {
        y: -50,
        opacity: 0,
        duration: 0.6,
        ease: "power3.in",
        stagger: 0.05
    })
        // The Signature Split Reveal
        .to('.top-panel', {
            yPercent: -100,
            duration: 1.2,
            ease: "expo.inOut"
        }, "-=0.2")
        .to('.bottom-panel', {
            yPercent: 100,
            duration: 1.2,
            ease: "expo.inOut"
        }, "-=1.2")
}
</script>

<style scoped>
.perspective-grid {
    background-image:
        linear-gradient(rgba(0, 210, 123, 0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 210, 123, 0.03) 1px, transparent 1px);
    background-size: 100px 100px;
    transform: perspective(1000px) rotateX(60deg) translateY(-20%);
    height: 200%;
}

@keyframes orbit {
    from {
        transform: rotate(0deg) rotateX(60deg);
    }

    to {
        transform: rotate(360deg) rotateX(60deg);
    }
}

@keyframes scanning-line {
    0% {
        transform: translateX(-100%);
    }

    100% {
        transform: translateX(100%);
    }
}

.animate-orbit {
    animation: orbit 10s linear infinite;
}

.animate-scanning-line {
    animation: scanning-line 2s linear infinite;
}

.fade-leave-active {
    transition: opacity 1s ease;
}

.fade-leave-to {
    opacity: 0;
}
</style>
