<template>
    <section ref="skillsRef" id="skills" class="py-60 bg-[#020408] relative overflow-hidden">
        <!-- Elite Technical Gravity Background -->
        <div class="absolute inset-0 z-0 pointer-events-none overflow-hidden">
            <!-- Orbiting Technical Rings -->
            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] border border-white/[0.03] rounded-full orbit-ring">
            </div>
            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[1200px] h-[1200px] border border-white/[0.02] rounded-full orbit-ring-reverse">
            </div>
        </div>


        <div class="max-w-7xl mx-auto px-6 relative z-10">
            <!-- Cinematic Header -->
            <div class="mb-40 space-y-4 header-content text-center md:text-left">
                <div class="flex items-center gap-4 justify-center md:justify-start reveal-item opacity-0">
                    <span class="w-12 h-[2px] bg-primary"></span>
                    <span
                        class="text-primary font-mono text-[10px] font-black tracking-[1em] uppercase">TECH_STACK_v5.0</span>
                </div>

                <h2
                    class="text-4xl sm:text-7xl md:text-[12rem] font-black tracking-tighter leading-[0.8] uppercase reveal-item opacity-0">
                    Technical <span class="text-transparent outline-text italic">Arsenal</span> <br />
                    <span class="text-primary">Super</span> Powers
                </h2>

                <div class="flex flex-col md:flex-row gap-10 md:items-center pt-10 reveal-item opacity-0">
                    <p class="text-white/30 text-base sm:text-lg max-w-xl font-medium leading-relaxed italic">
                        Forging <span class="text-white">high-performance systems</span> with a relentless focus on
                        scalable architecture and <span class="text-primary">pixel-perfect implementation</span>.
                    </p>
                    <div class="hidden md:block w-px h-16 bg-white/10"></div>
                    <div class="flex flex-col">
                        <span
                            class="text-[9px] font-mono text-white/20 uppercase tracking-[0.4em] mb-1">NODES_IDENTIFIED</span>
                        <span class="text-xl sm:text-3xl font-black text-primary italic">{{ skillsList.length
                        }}.00_STABLE</span>
                    </div>
                </div>
            </div>

            <!-- Elite Nexus Matrix (The Modern Skill Design) -->
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-y-12 sm:gap-y-24 gap-x-12 skills-matrix">
                <div v-for="(skill, index) in skillsList" :key="index"
                    class="nexus-node group relative cursor-crosshair"
                    :class="{ 'featured-skill': (index + 1) % 5 === 3 }">


                    <div class="relative z-10 flex flex-col items-center">
                        <!-- Node Core -->
                        <div class="relative flex items-center justify-center mb-8 transition-all duration-700"
                            :class="(index + 1) % 5 === 3 ? 'w-32 h-32 sm:w-40 sm:h-40 md:w-52 md:h-52' : 'w-24 h-24 sm:w-32 sm:h-32 md:w-40 md:h-40'">
                            <!-- Rotating Technical Border -->
                            <div
                                class="absolute inset-0 border-[0.5px] border-white/5 rounded-full group-hover:border-primary/40 transition-colors duration-700">
                            </div>
                            <div
                                class="absolute inset-2 border-[0.5px] border-white/10 rounded-full border-dashed animate-[spin_10s_linear_infinite] group-hover:border-primary transition-colors">
                            </div>

                            <!-- Static Center Node -->
                            <div class="rounded-full bg-white/[0.02] border border-white/10 flex items-center justify-center text-white/20 group-hover:text-primary transition-all duration-700 overflow-hidden group-hover:border-primary/30 group-hover:bg-primary/5"
                                :class="(index + 1) % 5 === 3 ? 'w-24 h-24 sm:w-28 sm:h-28 md:w-36 md:h-36' : 'w-16 h-16 sm:w-20 sm:h-20 md:w-24 md:h-24'">
                                <img :src="skill.logo" :alt="skill.name"
                                    class="object-contain relative z-10 group-hover:scale-110 transition-transform duration-700 opacity-80 group-hover:opacity-100"
                                    :class="(index + 1) % 5 === 3 ? 'w-12 h-12 sm:w-16 sm:h-16 md:w-20 md:h-20' : 'w-10 h-10 sm:w-12 sm:h-12 md:w-14 md:h-14'" />
                                <!-- Holographic Scanning line inside node -->
                                <div
                                    class="absolute inset-0 bg-gradient-to-b from-transparent via-primary/20 to-transparent -translate-y-full group-hover:translate-y-full transition-transform duration-1000">
                                </div>
                            </div>

                            <!-- Geometric Accents -->
                            <div
                                class="absolute -top-2 -right-2 w-4 h-4 border-t border-r border-white/10 group-hover:border-primary transition-colors">
                            </div>
                            <div
                                class="absolute -bottom-2 -left-2 w-4 h-4 border-b border-l border-white/10 group-hover:border-primary transition-colors">
                            </div>

                            <!-- Featured Badge -->
                            <div v-if="(index + 1) % 5 === 3"
                                class="absolute -top-6 left-1/2 -translate-x-1/2 px-4 py-1 bg-primary/10 border border-primary/30 rounded-full">
                                <span
                                    class="text-[8px] font-mono font-black text-primary uppercase tracking-wider">FEATURED</span>
                            </div>
                        </div>

                        <!-- Skill Metadata -->
                        <div class="text-center space-y-2">
                            <span
                                class="text-[9px] font-mono text-white/20 uppercase tracking-[0.4em] block group-hover:text-primary transition-colors">LVL_{{
                                    skill.strength * 20 }}%</span>
                            <h3 class="font-black uppercase italic tracking-tighter text-white/40 group-hover:text-white transition-all duration-500 scale-95 group-hover:scale-100"
                                :class="(index + 1) % 5 === 3 ? 'text-2xl sm:text-3xl md:text-4xl' : 'text-xl sm:text-2xl md:text-3xl'">
                                {{ skill.name }}
                            </h3>
                        </div>
                    </div>

                    <!-- Pinned Label (Hidden, reveals on scroll/hover) -->
                    <div
                        class="absolute -top-10 left-1/2 -translate-x-1/2 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none">
                        <span
                            class="text-[8px] font-mono bg-primary text-dark px-3 py-1 rounded-full font-black uppercase">SYSTEM_STABLE</span>
                    </div>
                </div>
            </div>

            <!-- Elite Operational HUD (Bottom) -->
            <div
                class="mt-60 flex flex-col md:flex-row justify-between items-center w-full pt-16 border-t border-white/5 reveal-item opacity-0">
                <div class="flex items-center gap-10">
                    <div v-for="tag in ['BACKEND_ARC', 'UI_LOGIC', 'SEC_LAYERS']" :key="tag"
                        class="flex items-center gap-3">
                        <div class="w-2 h-2 rounded-full bg-primary/40 animate-pulse"></div>
                        <span class="text-[9px] font-mono text-white/20 tracking-[0.4em] uppercase font-bold">{{ tag
                        }}</span>
                    </div>
                </div>

                <div
                    class="mt-10 md:mt-0 text-right font-mono text-[10px] text-white/10 italic tracking-widest leading-relaxed uppercase">
                    [ ARCHITECT_ACCESS_PROTOCOL_ACTIVE ] <br />
                    CORE_SYSTEM_STATUS: <span class="text-primary opacity-50">NOMINAL_OPTIMIZED</span>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import {
    CpuIcon, MonitorIcon, ServerIcon, ZapIcon, LayoutIcon,
    WindIcon, DatabaseIcon, Code2Icon, LayersIcon, GithubIcon,
    TerminalIcon, BoxIcon, SettingsIcon, ShieldIcon
} from 'lucide-vue-next'
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
    { name: 'Tailwind CSS', logo: 'https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg', strength: 5 },
    { name: 'Node.js', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg', strength: 5 },
    { name: 'HTML5', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg', strength: 5 },
    { name: 'CSS3', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg', strength: 5 },

    { name: 'Git', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', strength: 5 },
    { name: 'Linux', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg', strength: 4 },
    { name: 'Docker', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg', strength: 4 },
    { name: 'Bootstrap', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg', strength: 4 },
    { name: 'TypeScript', logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg', strength: 5 }
]

onMounted(() => {
    const ctx = gsap.context(() => {
        // 1. Cinematic Header Parallax & Reveal
        const headerTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.header-content',
                start: 'top 85%',
                end: 'bottom 10%',
                toggleActions: 'play reverse play reverse'
            }
        })

        headerTl.to('.reveal-item', {
            opacity: 1,
            y: 0,
            duration: 1.5,
            stagger: 0.2,
            ease: 'expo.out'
        })

        // 2. Background Text Parallax (Opposite directions)
        gsap.to('.parallax-bg-text-1', {
            scrollTrigger: {
                trigger: '#skills',
                start: 'top bottom',
                end: 'bottom top',
                scrub: 1
            },
            x: -200,
            opacity: 0.1
        })

        gsap.to('.parallax-bg-text-2', {
            scrollTrigger: {
                trigger: '#skills',
                start: 'top bottom',
                end: 'bottom top',
                scrub: 1
            },
            x: 200,
            opacity: 0.1
        })

        // 3. Matrix Nodes Kinetic Entrance
        gsap.from('.nexus-node', {
            scrollTrigger: {
                trigger: '.skills-matrix',
                start: 'top 80%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            },
            scale: 0.5,
            opacity: 0,
            y: 100,
            rotationY: 45,
            duration: 1.2,
            stagger: {
                each: 0.08,
                grid: 'auto',
                from: 'center'
            },
            ease: 'expo.out'
        })

        // 4. Orbit Rings Parallax
        gsap.to('.orbit-ring', {
            scrollTrigger: { trigger: '#skills', scrub: 1 },
            rotation: 360,
            scale: 1.2
        })

        gsap.to('.orbit-ring-reverse', {
            scrollTrigger: { trigger: '#skills', scrub: 1 },
            rotation: -360,
            scale: 0.8
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

/* Custom Cursor support if needed */
.cursor-crosshair {
    cursor: crosshair;
}
</style>
