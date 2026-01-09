<template>
    <section ref="skillsRef" id="skills" class="py-40 bg-[#020408] relative overflow-hidden">
        <!-- Elite Technical Gravity Background -->
        <div class="absolute inset-0 z-0 pointer-events-none overflow-hidden">
            <!-- Grid Texture -->
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_0%,#000_70%,transparent_100%)]">
            </div>

            <!-- Orbiting Technical Rings -->
            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] border border-white/[0.03] rounded-full orbit-ring">
            </div>
            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[1200px] h-[1200px] border border-white/[0.02] rounded-full orbit-ring-reverse">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <!-- Header Section (Massive Typography) -->
            <div class="mb-32 header-content">
                <div class="flex items-center gap-4 mb-6 reveal-meta opacity-0">
                    <span class="w-12 h-[1px] bg-primary/40"></span>
                    <span
                        class="text-[10px] font-mono font-black text-primary tracking-[0.6em] uppercase animate-pulse">
                        // TECH_STACK_v5.0
                    </span>
                </div>

                <!-- SCROLL-CONTROLLED KINETIC HEADER -->
                <h2
                    class="text-4xl sm:text-6xl md:text-[8rem] font-black italic uppercase leading-[0.85] tracking-tighter text-white mb-12 perspective-[1000px]">
                    <div class="overflow-hidden">
                        <span class="block reveal-text origin-bottom">TECHNICAL</span>
                    </div>
                    <div class="overflow-hidden">
                        <span class="block text-primary reveal-text origin-bottom">ARSENAL</span>
                    </div>
                    <div class="overflow-hidden flex items-center gap-6 mt-2">
                        <span class="block text-transparent reveal-text origin-bottom"
                            style="-webkit-text-stroke: 1px rgba(255,255,255,0.2);">SUPER</span>
                        <span
                            class="hidden md:block h-[1px] flex-1 bg-white/10 reveal-line origin-left scale-x-0"></span>
                    </div>
                    <div class="overflow-hidden">
                        <span class="block text-white reveal-text origin-bottom">POWERS</span>
                    </div>
                </h2>
            </div>

            <!-- Mobile View: Grid Matrix -->
            <div class="block md:hidden">
                <div class="grid grid-cols-2 gap-6 skills-matrix-mobile">
                    <div v-for="(skill, index) in skillsList" :key="index"
                        class="nexus-node-mobile group relative flex flex-col items-center">
                        <div
                            class="w-20 h-20 rounded-full bg-white/[0.03] border border-white/10 flex items-center justify-center mb-3 group-hover:border-primary/50 group-hover:bg-primary/10 transition-all duration-300">
                            <img :src="skill.logo" :alt="skill.name"
                                class="w-10 h-10 object-contain grayscale group-hover:grayscale-0 transition-all duration-300" />
                        </div>
                        <span class="text-xs font-bold text-white/50 group-hover:text-white uppercase tracking-wider">{{
                            skill.name }}</span>
                    </div>
                </div>
            </div>

            <!-- Desktop View: Planetary Orbit System -->
            <div
                class="hidden md:block relative h-[1000px] -mt-32 orbit-ring-container perspective-[1000px] overflow-visible">

                <!-- Center Core -->
                <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 z-20">
                    <div
                        class="w-32 h-32 rounded-full bg-[#020408] border border-primary/30 flex items-center justify-center relative shadow-[0_0_50px_rgba(0,210,123,0.2)]">
                        <div class="absolute inset-0 rounded-full border border-primary/20 animate-ping opacity-20">
                        </div>
                        <div class="text-center">
                            <span class="block text-3xl font-black text-white tracking-tighter">CORE</span>
                            <span
                                class="block text-[8px] font-mono text-primary tracking-[0.2em] uppercase">SYSTEM</span>
                        </div>
                    </div>
                </div>

                <!-- Inner Orbit Ring (5 Items) -->
                <!-- Ring rotates clockwise -->
                <div
                    class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[500px] h-[500px] rounded-full border border-white/5 animate-[spin_25s_linear_infinite] hover:[animation-play-state:paused] z-10">
                    <div v-for="(skill, index) in innerOrbitSkills" :key="skill.name"
                        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-24 h-24"
                        :style="`transform: rotate(${index * (360 / 5)}deg) translate(250px) rotate(-${index * (360 / 5)}deg)`">

                        <!-- Counter-rotate item to keep upright -->
                        <div class="w-full h-full animate-[spin_25s_linear_infinite_reverse]">
                            <div
                                class="w-24 h-24 rounded-full bg-[#080c14] border border-white/10 flex items-center justify-center hover:scale-125 hover:border-primary hover:shadow-[0_0_30px_rgba(0,210,123,0.3)] transition-all duration-500 cursor-pointer group relative">
                                <img :src="skill.logo" :alt="skill.name"
                                    class="w-12 h-12 object-contain filter grayscale group-hover:grayscale-0 transition-all duration-500" />

                                <!-- Tooltip -->
                                <div
                                    class="absolute -bottom-8 left-1/2 -translate-x-1/2 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                                    <span
                                        class="text-xs font-bold text-white uppercase tracking-widest bg-black/80 px-2 py-1 rounded whitespace-nowrap">{{
                                            skill.name }}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Outer Orbit Ring (Remaining Items) -->
                <!-- Ring rotates counter-clockwise -->
                <div
                    class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] rounded-full border border-white/5 animate-[spin_40s_linear_infinite_reverse] hover:[animation-play-state:paused] z-0">
                    <div v-for="(skill, index) in outerOrbitSkills" :key="skill.name"
                        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-20 h-20"
                        :style="`transform: rotate(${index * (360 / 10)}deg) translate(400px) rotate(-${index * (360 / 10)}deg)`">

                        <!-- Counter-rotate item (clockwise this time because ring is counter-clockwise) -->
                        <div class="w-full h-full animate-[spin_40s_linear_infinite]">
                            <div
                                class="w-20 h-20 rounded-full bg-[#080c14] border border-white/10 flex items-center justify-center hover:scale-125 hover:border-primary hover:shadow-[0_0_30px_rgba(0,210,123,0.3)] transition-all duration-500 cursor-pointer group relative">
                                <img :src="skill.logo" :alt="skill.name"
                                    class="w-10 h-10 object-contain filter grayscale group-hover:grayscale-0 transition-all duration-500" />

                                <!-- Tooltip -->
                                <div
                                    class="absolute -bottom-8 left-1/2 -translate-x-1/2 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                                    <span
                                        class="text-[10px] font-bold text-white uppercase tracking-widest bg-black/80 px-2 py-1 rounded whitespace-nowrap">{{
                                            skill.name }}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>

            <!-- Elite Operational HUD (Bottom) -->
            <div
                class="mt-20 border-t border-white/5 pt-8 flex items-center justify-between text-[10px] font-mono text-white/20 uppercase tracking-widest reveal-item opacity-0">
                <div class="flex items-center gap-10">
                    <div v-for="tag in ['ORBITAL_VELOCITY: 2400', 'GRAVITY: 1G', 'SEC_LAYERS']" :key="tag"
                        class="flex items-center gap-3">
                        <div class="w-2 h-2 rounded-full bg-primary/40 animate-pulse"></div>
                        <span class="text-[9px] font-mono text-white/20 tracking-[0.4em] uppercase font-bold">{{ tag
                            }}</span>
                    </div>
                </div>

                <div
                    class="text-right font-mono text-[10px] text-white/10 italic tracking-widest leading-relaxed uppercase">
                    [ SYSTEM_ROTATION_ACTIVE ] <br />
                    CORE_STATUS: <span class="text-primary opacity-50">STABLE</span>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const skillsRef = ref(null)

const skillsList = [
    { name: 'Laravel', logo: 'https://cdn.worldvectorlogo.com/logos/laravel-2.svg', strength: 5 },
    { name: 'Vue.js', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg', strength: 5 },
    { name: 'Antigravity', logo: 'https://www.gstatic.com/lamda/images/gemini_sparkle_v002_d4735304ff6292a690345.svg', strength: 5 },
    { name: 'JavaScript', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg', strength: 5 },
    { name: 'React', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg', strength: 5 },

    { name: 'Next.js', logo: 'https://cdn.worldvectorlogo.com/logos/next-js.svg', strength: 5 },
    { name: 'Tailwind', logo: 'https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg', strength: 5 },
    { name: 'Node.js', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg', strength: 5 },
    { name: 'HTML5', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg', strength: 5 },
    { name: 'CSS3', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg', strength: 5 },

    { name: 'Git', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', strength: 5 },
    { name: 'Linux', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg', strength: 4 },
    { name: 'Docker', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg', strength: 4 },
    { name: 'Bootstrap', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg', strength: 4 },
    { name: 'TypeScript', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg', strength: 5 }
]

const innerOrbitSkills = computed(() => skillsList.slice(0, 5))
const outerOrbitSkills = computed(() => skillsList.slice(5))

onMounted(() => {
    const ctx = gsap.context(() => {
        // Modern Kinetic Text Reveal (Auto-Play on Enter)
        const headerTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.header-content',
                start: 'top 85%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            }
        })

        // Reveal Metadata
        gsap.to('.reveal-meta', {
            opacity: 1,
            duration: 1,
            scrollTrigger: {
                trigger: '.header-content',
                start: 'top 90%',
                toggleActions: 'play none none reverse'
            }
        })

        // Kinetic Text Masks
        // Start from below (y: 100%) and skewed, animate to 0
        headerTl.from('.reveal-text', {
            y: '130%',
            skewY: 10,
            opacity: 0,
            stagger: 0.1,
            duration: 1.2,
            ease: 'expo.out'
        })
            .to('.reveal-line', {
                scaleX: 1,
                duration: 0.8,
                ease: 'expo.out'
            }, '-=0.8')


        // Mobile Grid Animation
        gsap.from('.nexus-node-mobile', {
            scrollTrigger: {
                trigger: '.skills-matrix-mobile',
                start: 'top 80%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            },
            scale: 0.5,
            opacity: 0,
            y: 50,
            duration: 0.8,
            stagger: 0.1,
            ease: 'back.out(1.7)'
        })

        // Orbit Interaction
        gsap.from('.orbit-ring-container', {
            scrollTrigger: {
                trigger: '#skills',
                start: 'top 60%',
                toggleActions: 'play reverse play reverse'
            },
            scale: 0.8,
            opacity: 0,
            duration: 1.5,
            ease: 'power4.out'
        })

    }, skillsRef.value)
})
</script>

<style scoped>
.outline-text {
    -webkit-text-stroke: 1.5px rgba(255, 255, 255, 0.1);
}

#skills {
    perspective: 2000px;
}

.nexus-node {
    transform-style: preserve-3d;
    transition: transform 0.5s cubic-bezier(0.23, 1, 0.32, 1);
}

.nexus-node:hover {
    transform: translateZ(50px) rotateX(5deg) rotateY(10deg);
}

.orbit-ring,
.orbit-ring-reverse {
    will-change: transform, opacity;
}

.cursor-crosshair {
    cursor: crosshair;
}
</style>
