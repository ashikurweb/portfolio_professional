<template>
    <section ref="expertiseRef" id="skills" class="py-32 bg-[#0A0F1E] relative overflow-hidden">
        <!-- Kinetic Background Particles (Decorative) -->
        <div class="absolute inset-0 opacity-20 pointer-events-none">
            <div v-for="i in 15" :key="i" class="particle absolute bg-primary/20 rounded-full"
                :style="getRandomParticleStyle()"></div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="header-animate mb-24">
                <div class="flex items-center gap-4 mb-6">
                    <div class="w-12 h-[1px] bg-primary"></div>
                    <span class="text-primary font-bold uppercase tracking-[0.4em] text-xs">Technical Arsenal</span>
                </div>
                <h2 class="text-6xl md:text-9xl font-black tracking-tighter leading-none text-white italic">
                    SUPER <br />
                    <span class="text-transparent stroke-text uppercase">Powers</span>
                </h2>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                <div v-for="(group, name) in expertise" :key="name"
                    class="group-card relative p-12 rounded-[2.5rem] bg-[#121829]/50 backdrop-blur-3xl border border-white/5 hover:border-primary/20 transition-all duration-700">

                    <div class="flex items-start justify-between mb-16">
                        <div>
                            <h3
                                class="text-4xl font-black mb-4 group-hover:text-primary transition-colors duration-500">
                                {{ name }}</h3>
                            <p class="text-gray-500 max-w-xs">{{ group.desc }}</p>
                        </div>
                        <div
                            class="group-icon w-20 h-20 rounded-[1.5rem] bg-white/5 border border-white/10 flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-dark transition-all duration-700 group-hover:rotate-[15deg]">
                            <component :is="group.icon" class="w-10 h-10" />
                        </div>
                    </div>

                    <div class="space-y-10">
                        <div v-for="skill in group.items" :key="skill.name" class="skill-item relative">
                            <div class="flex justify-between items-end mb-4">
                                <span class="text-xl font-bold text-white/80">{{ skill.name }}</span>
                                <span class="text-primary font-black text-2xl italic tabular-nums">{{ skill.level
                                    }}%</span>
                            </div>

                            <!-- GSAP Animated Progress Line -->
                            <div class="h-[2px] w-full bg-white/5 relative overflow-hidden">
                                <div class="progress-bar absolute top-0 left-0 h-full bg-gradient-to-r from-primary to-secondary"
                                    :data-level="skill.level"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { Monitor, Server, Palette, Terminal } from 'lucide-vue-next'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const expertiseRef = ref(null)

const expertise = {
    'Frontend': {
        icon: Monitor,
        desc: 'Crafting immersive user interfaces with speed and precision.',
        items: [
            { name: 'Vue 3 / Nuxt', level: 95 },
            { name: 'React / Next.js', level: 88 },
            { name: 'Tailwind CSS', level: 98 },
        ]
    },
    'Backend': {
        icon: Server,
        desc: 'Architecting scalable server-side systems and databases.',
        items: [
            { name: 'Node / Express', level: 85 },
            { name: 'Python / Django', level: 75 },
            { name: 'PostgreSQL', level: 80 },
        ]
    }
}

const getRandomParticleStyle = () => {
    const size = Math.random() * 4 + 1
    return {
        width: `${size}px`,
        height: `${size}px`,
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
    }
}

onMounted(() => {
    const ctx = gsap.context(() => {
        // Header Animation
        gsap.from('.header-animate', {
            scrollTrigger: {
                trigger: '.header-animate',
                start: 'top 80%',
            },
            y: 100,
            opacity: 0,
            duration: 1.5,
            ease: 'power4.out'
        })

        // Cards Staggered Slide In
        gsap.from('.group-card', {
            scrollTrigger: {
                trigger: '.group-card',
                start: 'top 85%',
            },
            x: (index) => index % 2 === 0 ? -100 : 100,
            opacity: 0,
            duration: 1.2,
            stagger: 0.3,
            ease: 'power3.out'
        })

        // Progress Bars Animation
        const bars = document.querySelectorAll('.progress-bar')
        bars.forEach(bar => {
            const level = bar.getAttribute('data-level')
            gsap.fromTo(bar,
                { width: '0%' },
                {
                    width: `${level}%`,
                    duration: 2,
                    ease: 'power2.inOut',
                    scrollTrigger: {
                        trigger: bar,
                        start: 'top 95%',
                    }
                }
            )
        })

        // Particle floating animation
        gsap.to('.particle', {
            y: 'random(-100, 100)',
            x: 'random(-100, 100)',
            duration: 'random(5, 15)',
            repeat: -1,
            yoyo: true,
            ease: 'sine.inOut'
        })
    }, expertiseRef.value)
})
</script>

<style scoped>
.stroke-text {
    -webkit-text-stroke: 1px rgba(255, 255, 255, 0.1);
}

.group-card:hover .stroke-text {
    -webkit-text-stroke: 1px var(--color-primary);
    opacity: 0.5;
}
</style>
