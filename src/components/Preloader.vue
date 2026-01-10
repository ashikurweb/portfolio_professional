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

                    <!-- Prismatic Liquid Aura (Luxury Abstract Design) -->
                    <div class="prismatic-system absolute inset-0 flex items-center justify-center">
                        <!-- Main Radiant Glow -->
                        <div
                            class="absolute w-[200%] h-[200%] bg-gradient-to-tr from-primary/20 via-blue-500/10 to-transparent blur-[120px] rounded-full animate-slow-spin">
                        </div>

                        <!-- Geometric Echoes (Ghosting Effect) -->
                        <div
                            class="echo-frame absolute inset-0 border border-primary/10 rounded-2xl rotate-12 reveal-element scale-150">
                        </div>
                        <div
                            class="echo-frame absolute inset-4 border border-white/5 rounded-xl -rotate-12 reveal-element scale-125">
                        </div>
                    </div>

                    <!-- The Integrated Logo Wrapper -->
                    <div class="logo-wrapper relative z-10 transform scale-75 opacity-0">
                        <!-- Actual Site Logo Component -->
                        <Logo class="!gap-0" />
                    </div>

                    <!-- Energy Core Beam -->
                    <div
                        class="absolute h-[1px] w-full bg-gradient-to-r from-transparent via-primary/40 to-transparent -translate-x-full scan-beam">
                    </div>
                </div>

            </div>

        </div>
    </Transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Logo from './Logo.vue'
import gsap from 'gsap'

const isLoaded = ref(false)

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

    // Fluid Aura Animations
    gsap.to('.echo-frame', {
        rotate: (i) => i === 0 ? 360 + 12 : -360 - 12,
        duration: 30,
        repeat: -1,
        ease: "none"
    })

    gsap.to('.echo-frame', {
        scale: (i) => 1.1 + (i * 0.1),
        opacity: (i) => 1 - (i * 0.5),
        duration: 4,
        repeat: -1,
        yoyo: true,
        ease: "sine.inOut"
    })

    // Scan Beam Cycle
    gsap.to('.scan-beam', {
        xPercent: 200,
        duration: 2,
        repeat: -1,
        ease: "power1.inOut"
    })

    // Auto Exit after a delay
    gsap.delayedCall(3, exitSequence)
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
    tl.to('.logo-viewport', {
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

.split-panel {
    will-change: transform;
}

@keyframes slow-spin {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }
}

.animate-slow-spin {
    animation: slow-spin 20s linear infinite;
}

.fade-leave-active {
    transition: opacity 0.8s ease;
}

.fade-leave-to {
    opacity: 0;
}
</style>
