<template>
    <Transition name="fade">
        <div v-if="!isLoaded"
            class="preloader-overlay fixed inset-0 z-[9999] bg-[#03050a] overflow-hidden flex items-center justify-center">

            <!-- High-End Split Panels -->
            <div
                class="split-panel top-panel absolute top-0 left-0 w-full h-1/2 bg-[#050810] border-b border-primary/5 shadow-[0_4px_30px_rgba(0,0,0,0.5)]">
            </div>
            <div
                class="split-panel bottom-panel absolute bottom-0 left-0 w-full h-1/2 bg-[#050810] border-t border-primary/5 shadow-[0_-4px_30px_rgba(0,0,0,0.5)]">
            </div>

            <!-- Dynamic Background Depth -->
            <div class="absolute inset-0 z-0 pointer-events-none overflow-hidden">
                <!-- Moving Gradient Orbs -->
                <div
                    class="absolute top-[-10%] left-[-5%] w-[60%] h-[60%] bg-primary/10 blur-[130px] rounded-full animate-drift">
                </div>
                <div
                    class="absolute bottom-[-10%] right-[-5%] w-[60%] h-[60%] bg-blue-600/10 blur-[130px] rounded-full animate-drift-reverse">
                </div>

                <!-- Noise and Grid Overlays -->
                <div class="absolute inset-0 noise-texture opacity-[0.03]"></div>
                <div class="absolute inset-0 opacity-[0.05]"
                    style="background-image: radial-gradient(var(--color-primary) 0.5px, transparent 0.5px); background-size: 30px 30px;">
                </div>
            </div>

            <!-- Central Content -->
            <div class="relative z-10 flex flex-col items-center">

                <!-- Ultra-Premium Abstract Logo -->
                <div class="logo-viewport relative w-48 h-48 flex items-center justify-center">

                    <!-- Outer Geometric Orbits (High-End GSAP Control) -->
                    <div
                        class="orbit-ring absolute w-full h-full border border-primary/20 rounded-full scale-0 reveal-element">
                    </div>
                    <div
                        class="orbit-ring-inner absolute w-3/4 h-3/4 border border-secondary/20 rounded-full scale-0 reveal-element">
                    </div>

                    <!-- The Integrated Logo Wrapper -->
                    <div class="logo-wrapper relative z-10 transform scale-75 opacity-0">
                        <!-- Liquid Glass Backdrop -->
                        <div
                            class="absolute inset-[-20px] bg-primary/5 backdrop-blur-xl rounded-[40%_60%_70%_30%/50%_50%_50%_50%] animate-morph">
                        </div>

                        <!-- Actual Site Logo Component -->
                        <Logo class="!gap-0" />
                    </div>

                    <!-- Energy Core Beam -->
                    <div
                        class="absolute h-[1px] w-full bg-gradient-to-r from-transparent via-primary/40 to-transparent -translate-x-full scan-beam">
                    </div>
                </div>

                <!-- Modern Scientific Progress -->
                <div class="progress-module mt-16 opacity-0 translate-y-8 flex flex-col items-center">
                    <div class="flex items-center gap-4 mb-4">
                        <span
                            class="text-[9px] font-mono tracking-[0.6em] text-primary lowercase animate-pulse">Initializing.Core</span>
                    </div>

                    <div class="flex items-baseline gap-0.5 mb-6">
                        <span class="text-6xl font-black italic tracking-tighter text-white tabular-nums counter-val">
                            {{ Math.floor(progress) }}
                        </span>
                        <span class="text-[14px] font-bold text-primary align-top mt-2">%</span>
                    </div>

                    <!-- Minimalist Progress Bar -->
                    <div class="w-64 h-[1px] bg-white/5 relative overflow-hidden">
                        <div class="absolute inset-y-0 left-0 bg-primary shadow-[0_0_15px_#00D27B] transition-all duration-300 ease-out"
                            :style="{ width: `${progress}%` }"></div>
                    </div>
                </div>
            </div>

            <!-- System Telemetry Corner (Unique Modern) -->
            <div class="absolute bottom-12 left-12 flex flex-col gap-1 opacity-0 meta-element">
                <span class="text-[8px] font-mono text-gray-800 tracking-widest">LOC: 23.8N_90.4E</span>
                <span class="text-[8px] font-mono text-gray-800 tracking-widest">PROTOCOL: SE-32</span>
            </div>
            <div class="absolute bottom-12 right-12 flex flex-col items-end gap-1 opacity-0 meta-element">
                <span class="text-[8px] font-mono text-gray-800 tracking-widest">EST. ARCHIVE 2024</span>
                <span class="text-[8px] font-mono text-gray-800 tracking-widest">SHARPER_UI_ENGINE</span>
            </div>

        </div>
    </Transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Logo from './Logo.vue'
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

    // Entrance Sequence
    tl.to('.reveal-element', {
        scale: 1,
        opacity: 1,
        duration: 1,
        stagger: 0.1,
        ease: "expo.out"
    })
        .to('.logo-wrapper', {
            opacity: 1,
            scale: 1.2,
            duration: 1.2,
            ease: "power4.out"
        }, "-=0.6")
        .to('.progress-module, .meta-element', {
            opacity: 1,
            y: 0,
            duration: 1,
            stagger: 0.1,
            ease: "power2.out"
        }, "-=0.8")

    // Signature Orbit Rotations (Clean GSAP)
    gsap.to('.orbit-ring', { rotate: 360, duration: 10, repeat: -1, ease: 'none' })
    gsap.to('.orbit-ring-inner', { rotate: -360, duration: 15, repeat: -1, ease: 'none' })

    // Scan Beam Cycle
    gsap.to('.scan-beam', {
        xPercent: 200,
        duration: 2,
        repeat: -1,
        ease: "power1.inOut"
    })

    // Percentage Counter
    gsap.to(progress, {
        value: 100,
        duration: 3,
        ease: "power2.inOut"
    })
})

const exitSequence = () => {
    const tl = gsap.timeline({
        onComplete: () => {
            isLoaded.value = true
            document.body.style.overflow = ''
            window.dispatchEvent(new CustomEvent('preloaderComplete'))
        }
    })

    // Dynamic Dissolve
    tl.to('.logo-viewport, .progress-module, .meta-element', {
        scale: 0.9,
        opacity: 0,
        duration: 0.5,
        ease: "power2.in",
        stagger: 0.05
    })

        // The User's Favorite Split Reveal
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
.noise-texture {
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

@keyframes morph {

    0%,
    100% {
        border-radius: 40% 60% 70% 30% / 50% 50% 50% 50%;
    }

    50% {
        border-radius: 60% 40% 30% 70% / 50% 50% 50% 50%;
        transform: rotate(180deg);
    }
}

.animate-morph {
    animation: morph 10s linear infinite;
}

.split-panel {
    will-change: transform;
}

.fade-leave-active {
    transition: opacity 0.8s ease;
}

.fade-leave-to {
    opacity: 0;
}
</style>
