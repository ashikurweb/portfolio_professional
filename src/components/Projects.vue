<template>
    <section id="projects" class="py-32 bg-[#020408] relative overflow-hidden">
        <!-- Background Elements -->
        <div class="absolute inset-0 pointer-events-none">
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_0%,#000_70%,transparent_100%)]">
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <!-- Header Section -->
            <div class="mb-20 projects-header">
                <div class="flex items-center gap-4 mb-6 project-label">
                    <span class="w-12 h-[1px] bg-primary/40"></span>
                    <span
                        class="text-[10px] font-mono font-black text-primary tracking-[0.6em] uppercase animate-pulse">
                        // PROJECT_ARCHIVE_v2.0
                    </span>
                </div>

                <h2
                    class="text-4xl sm:text-6xl md:text-[8rem] font-black italic uppercase leading-[0.85] tracking-tighter text-white mb-12">
                    <div class="overflow-hidden">
                        <span class="block project-title-1">SELECTED</span>
                    </div>
                    <div class="overflow-hidden flex items-center gap-6">
                        <span class="block text-transparent project-title-2"
                            style="-webkit-text-stroke: 1px rgba(255,255,255,0.2);">WORKS</span>
                        <span class="hidden md:block h-[1px] flex-1 bg-white/10"></span>
                    </div>
                </h2>

                <!-- Control Panel (Tabs) -->
                <div class="flex flex-wrap gap-4 items-center project-tabs">
                    <button v-for="tab in tabs" :key="tab" @click="activeTab = tab"
                        class="group relative px-6 py-3 overflow-hidden">
                        <!-- Active/Inactive Border -->
                        <div class="absolute inset-0 border border-white/10 skew-x-[-12deg] transition-all duration-300"
                            :class="activeTab === tab ? 'bg-primary border-primary' : 'group-hover:border-primary/50'">
                        </div>

                        <span
                            class="relative z-10 text-xs font-black uppercase tracking-widest transition-colors duration-300"
                            :class="activeTab === tab ? 'text-black' : 'text-white/40 group-hover:text-white'">
                            {{ tab }}
                        </span>
                    </button>
                </div>
            </div>

            <!-- Projects Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div v-for="(project, index) in filteredProjects" :key="project.id"
                    class="project-card group relative bg-[#080c14] border border-white/5 rounded-3xl overflow-hidden hover:border-primary/40 hover:-translate-y-1 hover:shadow-2xl hover:shadow-primary/5 transition-all duration-500">

                    <!-- Project Image/Preview -->
                    <div class="aspect-[16/10] overflow-hidden relative">
                        <!-- Image Gradient Overlay -->
                        <div
                            class="absolute inset-0 bg-gradient-to-t from-[#080c14] via-transparent to-transparent opacity-60 z-10 pointer-events-none">
                        </div>

                        <img v-if="project.image" :src="project.image" :alt="project.title"
                            class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-[1s] ease-in-out" />

                        <div v-else
                            class="w-full h-full bg-[#05080F] flex items-center justify-center group-hover:bg-[#070B16] transition-colors">
                            <span
                                class="text-6xl font-black text-white/5 group-hover:text-primary/10 transition-colors uppercase select-none">
                                {{ project.title.substring(0, 2) }}
                            </span>
                        </div>

                        <!-- Action Buttons Overlay -->
                        <div
                            class="absolute inset-0 z-20 flex items-center justify-center gap-3 opacity-0 group-hover:opacity-100 transition-all duration-500 bg-black/40 backdrop-blur-[3px]">

                            <!-- Button 1: Live System -->
                            <a :href="project.liveLink" target="_blank"
                                class="flex items-center gap-2 px-6 py-3 rounded-full bg-primary text-[#020408] font-bold uppercase text-[10px] tracking-[0.2em] hover:bg-white hover:scale-105 transition-all duration-300 transform translate-y-4 group-hover:translate-y-0 active:scale-95 shadow-lg shadow-black/20">
                                <ExternalLinkIcon size="14" stroke-width="2.5" />
                                <span>Preview</span>
                            </a>

                            <!-- Button 2: Code Repo -->
                            <a :href="project.githubLink" target="_blank"
                                class="flex items-center gap-2 px-6 py-3 rounded-full bg-white/10 text-white font-bold uppercase text-[10px] tracking-[0.2em] border border-white/20 hover:border-primary hover:bg-black/50 hover:text-primary transition-all duration-300 transform translate-y-4 group-hover:translate-y-0 delay-75 active:scale-95 backdrop-blur-md">
                                <GithubIcon size="14" />
                                <span>Code</span>
                            </a>

                        </div>
                    </div>

                    <!-- Content Info -->
                    <div class="p-8 pt-6 relative z-10">
                        <div class="flex flex-col gap-3 mb-4">
                            <span class="text-primary text-[10px] font-mono uppercase tracking-[0.25em] pl-0.5">{{
                                project.category }}</span>
                            <h3
                                class="text-2xl font-bold text-white leading-tight group-hover:text-primary/90 transition-colors duration-300">
                                {{ project.title }}</h3>
                        </div>

                        <p class="text-sm text-white/40 leading-relaxed mb-6 font-medium">
                            {{ project.desc }}
                        </p>

                        <!-- Tags (Pills) -->
                        <div class="flex flex-wrap gap-2">
                            <span v-for="tag in project.tags" :key="tag"
                                class="px-3 py-1 rounded-full bg-white/[0.03] border border-white/5 text-[10px] font-semibold text-white/40 uppercase tracking-wider group-hover:border-primary/20 group-hover:text-white/60 transition-colors duration-300">
                                {{ tag }}
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { GithubIcon, ExternalLinkIcon } from 'lucide-vue-next'

const tabs = ['All', 'UI/UX Design', 'Web Dev', 'Branding']
const activeTab = ref('All')

const projects = [
    {
        id: 1,
        title: 'E-Commerce Platform',
        category: 'Web Dev',
        desc: 'A full-featured shopping experience with real-time inventory.',
        tags: ['Vue 3', 'Node.js', 'PostgreSQL'],
        image: '/assets/project1.png',
        liveLink: '#',
        githubLink: '#'
    },
    {
        id: 2,
        title: 'Fitness Tracker App',
        category: 'UI/UX Design',
        desc: 'Modern interface for tracking daily activities and health goals.',
        tags: ['Figma', 'Prototyping'],
        image: '/assets/project2.png',
        liveLink: '#',
        githubLink: '#'
    },
    {
        id: 3,
        title: 'Brand Identity Design',
        category: 'Branding',
        desc: 'Developing a unique visual language for a tech startup.',
        tags: ['Identity', 'Guidelines'],
        image: '/assets/project3.png',
        liveLink: '#',
        githubLink: '#'
    },
    {
        id: 4,
        title: 'Real Estate Portal',
        category: 'Web Dev',
        desc: 'Interactive property searching and virtual tours.',
        tags: ['Vite', 'Firebase'],
        image: '/assets/project4.png',
        liveLink: '#',
        githubLink: '#'
    },
    {
        id: 5,
        title: 'Food Delivery App',
        category: 'UI/UX Design',
        desc: 'Streamlined UX for ordering and real-time delivery tracking.',
        tags: ['Mobile Design', 'UI Kit'],
        image: '/assets/project2.png',
        liveLink: '#',
        githubLink: '#'
    },
    {
        id: 6,
        title: 'Dashboard UI',
        category: 'UI/UX Design',
        desc: 'Complex data visualization and management system.',
        tags: ['React', 'Charts'],
        image: '/assets/project1.png',
        liveLink: '#',
        githubLink: '#'
    },
]

const filteredProjects = computed(() => {
    if (activeTab.value === 'All') return projects
    return projects.filter(p => p.category === activeTab.value)
})

import { onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
    // Header Reveal Animation
    const headerTl = gsap.timeline({
        scrollTrigger: {
            trigger: '.projects-header',
            start: 'top 85%',
            end: 'bottom 20%',
            toggleActions: 'play reverse play reverse'
        }
    })

    headerTl.from('.project-title-1', {
        x: -100,
        opacity: 0,
        duration: 1.2,
        ease: 'expo.out'
    })
        .from('.project-title-2', {
            x: 100,
            opacity: 0,
            duration: 1.2,
            skewX: 10,
            ease: 'expo.out'
        }, '-=1')
        .from('.project-label', {
            y: 20,
            opacity: 0,
            duration: 0.8,
            ease: 'power3.out'
        }, '-=0.8')
        .from('.project-tabs button', {
            y: 30,
            opacity: 0,
            stagger: 0.1,
            duration: 1,
            ease: 'back.out(1.7)'
        }, '-=1')

    // Project Cards Zoom-In on Scroll
    gsap.utils.toArray('.project-card').forEach((card) => {
        gsap.from(card, {
            scale: 0.9,
            opacity: 0,
            y: 50,
            duration: 1,
            ease: 'power4.out',
            scrollTrigger: {
                trigger: card,
                start: 'top 90%',
                toggleActions: 'play reverse play reverse'
            }
        })
    })
})
</script>
