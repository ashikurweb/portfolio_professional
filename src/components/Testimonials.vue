<template>
    <section id="testimonials" class="relative pt-32 pb-48 overflow-hidden bg-[#020408]">
        <!-- Ultra-Modern Mesh Gradient Background -->
        <div class="absolute inset-0 pointer-events-none">
            <div
                class="absolute top-[10%] left-[-10%] w-[40%] h-[40%] bg-primary/10 rounded-full blur-[140px] animate-pulse">
            </div>
            <div class="absolute bottom-[10%] right-[-10%] w-[30%] h-[30%] bg-blue-500/5 rounded-full blur-[100px]">
            </div>
            <div class="absolute inset-0 opacity-[0.02]"
                style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); background-size: 40px 40px;">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <!-- Sleek Header Design -->
            <div class="flex flex-col md:flex-row md:items-end justify-between gap-8 mb-24">
                <div class="space-y-4">
                    <div class="flex items-center gap-3 reveal-subtext">
                        <span class="w-8 h-[1px] bg-primary"></span>
                        <span class="text-[10px] uppercase tracking-[0.6em] text-primary font-bold">Client Echo</span>
                    </div>
                    <h2 class="text-5xl md:text-8xl font-black text-white leading-[0.9] tracking-tighter">
                        <div class="overflow-hidden">
                            <span class="block reveal-title-elite italic">ELITE</span>
                        </div>
                        <div class="overflow-hidden">
                            <span class="block title-outline text-transparent reveal-title-feedback italic"
                                style="-webkit-text-stroke: 1px rgba(255,255,255,0.2)">FEEDBACK.</span>
                        </div>
                    </h2>
                </div>
                <div class="overflow-hidden">
                    <p
                        class="max-w-[300px] text-white/40 text-sm font-medium leading-relaxed border-l border-white/10 pl-6 mb-2 reveal-desc">
                        Collaborating with global leaders to build the next generation of digital infrastructure.
                    </p>
                </div>
            </div>

            <!-- Modern Testimonial Stage -->
            <div class="relative min-h-[850px] md:min-h-[750px] lg:min-h-[600px] mb-12">
                <div v-for="(testimonial, index) in testimonials" :key="index"
                    class="testimonial-slice absolute inset-0 grid lg:grid-cols-2 gap-16 lg:gap-24 items-start lg:items-center opacity-0 pointer-events-none"
                    :class="{ 'active-slice': activeIndex === index }">

                    <!-- Visual Side: Image + Decorative Elements (Left on Desktop) -->
                    <div
                        class="relative order-2 lg:order-1 perspective-2000 w-full max-w-[500px] mx-auto lg:ml-0 flex items-center">
                        <!-- New Vertical Counter Element - Moved inside the container to prevent clipping -->
                        <div
                            class="absolute left-0 top-1/2 -translate-y-1/2 flex flex-col items-center gap-4 py-8 border-l border-white/10 hidden lg:flex reveal-counter opacity-0 z-20">
                            <span
                                class="text-[9px] font-mono text-primary uppercase tracking-[0.5em] [writing-mode:vertical-lr] rotate-180">Index_Record</span>
                            <span class="text-4xl font-black text-white italic">0{{ index + 1 }}</span>
                        </div>

                        <!-- Image Wrapper with Padding to make room for the counter -->
                        <div class="image-wrapper relative z-10 opacity-0 transform-style-3d lg:pl-20 w-full">
                            <div
                                class="image-container relative aspect-[4/5] overflow-hidden rounded-sm grayscale transition-all duration-1000 group-hover:grayscale-0 bg-[#161B2E]">
                                <img :src="testimonial.image" :alt="testimonial.name"
                                    class="w-full h-full object-cover scale-110">
                                <!-- Modern Shutter Reveal Overlay -->
                                <div class="shutter-overlay absolute inset-0 bg-[#020408] z-20"></div>
                                <div class="absolute inset-0 bg-primary/10 mix-blend-overlay"></div>
                            </div>
                            <!-- Floating Data Tag -->
                            <div
                                class="absolute -bottom-4 -right-4 bg-primary px-4 py-2 z-30 shadow-2xl skew-x-[-12deg]">
                                <span class="text-[10px] font-black text-black uppercase italic tracking-widest">{{
                                    testimonial.company }}</span>
                            </div>
                        </div>

                        <!-- Abstract Geometry moved to align with image -->
                        <div class="absolute top-0 right-0 w-32 h-32 border-r border-t border-primary/30 z-0"></div>
                        <div class="absolute bottom-0 left-20 w-32 h-32 border-l border-b border-white/10 z-0"></div>
                    </div>

                    <!-- Content Side: The Quote (Right on Desktop) -->
                    <div class="space-y-12 order-1 lg:order-2 max-w-xl">
                        <div class="relative">
                            <p
                                class="quote-text text-2xl md:text-3xl lg:text-4xl font-black text-white/90 leading-[1.3] italic opacity-0">
                                "{{ testimonial.content }}"
                            </p>
                        </div>

                        <div class="meta-section opacity-0">
                            <div class="flex items-center gap-6">
                                <div class="h-[2px] w-12 bg-primary"></div>
                                <div>
                                    <h4 class="text-xl font-black text-white tracking-tight uppercase italic">{{
                                        testimonial.name }}</h4>
                                    <p class="text-primary text-[10px] uppercase tracking-[0.4em] font-bold mt-1">{{
                                        testimonial.role }}</p>
                                </div>
                            </div>
                        </div>

                        <!-- Progress Interaction & Controls -->
                        <div class="flex flex-col gap-10 pt-12 relative z-[99]">
                            <div class="progress-track w-full h-[2px] bg-white/5 relative overflow-hidden">
                                <div class="progress-bar absolute inset-y-0 left-0 bg-primary shadow-[0_0_20px_#00D27B]"
                                    style="width: 0%"></div>
                            </div>

                            <div class="flex items-center justify-between">
                                <!-- Navigation Counters -->
                                <div class="flex gap-3">
                                    <div v-for="(_, i) in testimonials.length" :key="i"
                                        class="w-12 h-[2px] transition-all duration-500"
                                        :class="activeIndex === i ? 'bg-primary' : 'bg-white/10'"></div>
                                </div>

                                <div class="flex gap-6">
                                    <button @click="prevSlide" class="nav-btn-magnetic group">
                                        <div
                                            class="w-16 h-16 rounded-full border border-white/10 flex items-center justify-center group-hover:border-primary group-hover:bg-primary/5 transition-all duration-500 overflow-hidden relative">
                                            <div
                                                class="absolute inset-0 bg-primary scale-0 group-hover:scale-100 transition-transform duration-500 opacity-10 rounded-full">
                                            </div>
                                            <svg class="w-6 h-6 text-white/40 group-hover:text-primary transition-colors relative z-10"
                                                fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                    d="M15 19l-7-7 7-7" />
                                            </svg>
                                        </div>
                                    </button>
                                    <button @click="nextSlide" class="nav-btn-magnetic group">
                                        <div
                                            class="w-16 h-16 rounded-full border border-white/10 flex items-center justify-center group-hover:border-primary group-hover:bg-primary/5 transition-all duration-500 overflow-hidden relative">
                                            <div
                                                class="absolute inset-0 bg-primary scale-0 group-hover:scale-100 transition-transform duration-500 opacity-10 rounded-full">
                                            </div>
                                            <svg class="w-6 h-6 text-white/40 group-hover:text-primary transition-colors relative z-10"
                                                fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                    d="M9 5l7 7-7 7" />
                                            </svg>
                                        </div>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const testimonials = [
    {
        name: 'Alexander Wright',
        role: 'CTO @ NEXUS LABS',
        company: 'NEXUS_LABS',
        content: "Ashikur's architectural vision transformed our legacy systems into high-speed digital ecosystems. Exceptional delivery.",
        image: '/src/assets/testimonial1.png'
    },
    {
        name: 'Sophia Martinez',
        role: 'CREATIVE DIRECTOR',
        company: 'PIXEL_PERFECT',
        content: "The kinetic interface he engineered didn't just meet our needs—it redefined our brand's digital presence entirely.",
        image: '/src/assets/testimonial2.png'
    },
    {
        name: 'Elena Volkov',
        role: 'LEAD ARCHITECT',
        company: 'CYBER_CORE',
        content: "Clean code, superior performance, and an agentic approach to problem-solving. A rare talent in modern engineering.",
        image: '/src/assets/testimonial3.png'
    }
]

const activeIndex = ref(0)
let isAnimating = false
let progressTl = null

const nextSlide = () => {
    if (isAnimating) return
    transition((activeIndex.value + 1) % testimonials.length)
}

const prevSlide = () => {
    if (isAnimating) return
    transition((activeIndex.value - 1 + testimonials.length) % testimonials.length)
}

const transition = (nextIndex) => {
    isAnimating = true
    if (progressTl) progressTl.kill()

    const current = document.querySelectorAll('.testimonial-slice')[activeIndex.value]
    const next = document.querySelectorAll('.testimonial-slice')[nextIndex]

    const tl = gsap.timeline({
        onComplete: () => {
            activeIndex.value = nextIndex
            isAnimating = false
            animateIn(next)
        }
    })

    // Sophisticated Outgoing Slide
    tl.to(current.querySelector('.quote-text'), { x: -150, skewX: 10, opacity: 0, duration: 0.8, ease: 'expo.in' })
        .to(current.querySelector('.image-wrapper'), { x: 150, skewX: -10, opacity: 0, duration: 0.8, ease: 'expo.in' }, "-=0.8")
        .to(current.querySelector('.reveal-counter'), { x: -50, opacity: 0, duration: 0.4 }, "-=0.6")
        .to(current.querySelector('.meta-section'), { opacity: 0, y: 20, duration: 0.4 }, "-=0.5")
        .set(current, { opacity: 0, pointerEvents: 'none' })
}

const animateIn = (target) => {
    gsap.set(target, { opacity: 1, pointerEvents: 'auto' })
    const shutter = target.querySelector('.shutter-overlay')
    const img = target.querySelector('img')

    const tl = gsap.timeline()

    // Kinetic Fluid Entrance
    tl.fromTo(target.querySelector('.image-wrapper'),
        { x: -150, skewX: 15, opacity: 0 },
        { x: 0, skewX: 0, opacity: 1, duration: 1.5, ease: 'expo.out' }
    )
        .to(shutter, { x: '100%', duration: 1.2, ease: 'expo.inOut' }, "-=1.2")
        .to(img, { scale: 1, duration: 1.5, ease: 'expo.out' }, "-=1.2")
        .fromTo(target.querySelector('.reveal-counter'),
            { x: -50, opacity: 0 },
            { x: 0, opacity: 1, duration: 1, ease: 'expo.out' }, "-=1")
        .fromTo(target.querySelector('.quote-text'),
            { x: 150, skewX: -15, opacity: 0 },
            { x: 0, skewX: 0, opacity: 1, duration: 1.5, ease: 'expo.out' }, "-=1.2")
        .fromTo(target.querySelector('.meta-section'),
            { y: 30, opacity: 0 },
            { y: 0, opacity: 1, duration: 1, ease: 'expo.out' }, "-=0.8")

    // Kinetic Auto-progress
    progressTl = gsap.fromTo(target.querySelector('.progress-bar'),
        { width: '0%' },
        { width: '100%', duration: 10, ease: 'none', onComplete: nextSlide }
    )
}

onMounted(() => {
    // Ultra-Powerful Header Reveal (Scroll Synced)
    const headerTl = gsap.timeline({
        scrollTrigger: {
            trigger: '#testimonials',
            start: 'top 95%',
            end: 'top 30%',
            scrub: 1,
        }
    })

    headerTl.from('.reveal-title-elite', {
        x: -300,
        skewX: 30,
        letterSpacing: '2em',
        opacity: 0,
        ease: 'power4.out',
    })
        .from('.reveal-title-feedback', {
            x: 300,
            skewX: -30,
            letterSpacing: '2em',
            opacity: 0,
            ease: 'power4.out',
        }, "-=0.8")
        .from('.reveal-subtext', {
            y: 50,
            opacity: 0,
            ease: 'power3.out',
        }, "-=0.6")
        .from('.reveal-desc', {
            scaleX: 0,
            transformOrigin: 'left',
            opacity: 0,
            ease: 'power3.out',
        }, "-=0.4")

    // Magnetic Buttons Physics
    const buttons = document.querySelectorAll('.nav-btn-magnetic')
    buttons.forEach(btn => {
        btn.addEventListener('mousemove', (e) => {
            const rect = btn.getBoundingClientRect()
            const x = e.clientX - rect.left - rect.width / 2
            const y = e.clientY - rect.top - rect.height / 2

            gsap.to(btn.querySelector('div'), {
                x: x * 0.5,
                y: y * 0.5,
                duration: 0.6,
                ease: 'power2.out'
            })
        })

        btn.addEventListener('mouseleave', () => {
            gsap.to(btn.querySelector('div'), {
                x: 0,
                y: 0,
                duration: 0.8,
                ease: 'elastic.out(1, 0.3)'
            })
        })
    })

    // Initial Slice Activation
    setTimeout(() => {
        const slices = document.querySelectorAll('.testimonial-slice')
        if (slices.length > 0) animateIn(slices[0])
    }, 500)
})
</script>

<style scoped>
.title-outline {
    -webkit-text-stroke: 1px rgba(255, 255, 255, 0.2);
}

.perspective-2000 {
    perspective: 2000px;
}

.transform-style-3d {
    transform-style: preserve-3d;
}

.testimonial-slice {
    transition: z-index 0.3s;
}

.active-slice {
    z-index: 10;
}

.nav-btn-magnetic {
    cursor: pointer;
    z-index: 99;
    padding: 10px;
    margin: -10px;
}
</style>
