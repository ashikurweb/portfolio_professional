<template>
    <section id="projects" class="py-20 bg-[#070B16]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <span class="text-primary font-bold uppercase tracking-widest text-sm mb-4 block">Portfolio</span>
                <h2 class="text-4xl md:text-5xl font-bold mb-6">Featured <span class="text-primary">Projects</span></h2>
                <p class="text-gray-400 max-w-2xl mx-auto">
                    Explore a selection of my recently completed projects, showcasing my expertise in various domains.
                </p>
            </div>

            <div class="flex justify-center flex-wrap gap-4 mb-12">
                <button v-for="tab in tabs" :key="tab" @click="activeTab = tab" :class="[
                    'px-6 py-2 rounded-full font-medium transition-all',
                    activeTab === tab ? 'bg-primary text-dark' : 'bg-white/5 text-gray-400 hover:text-white hover:bg-white/10'
                ]">
                    {{ tab }}
                </button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div v-for="project in filteredProjects" :key="project.id"
                    class="group relative bg-[#161B2E] rounded-3xl overflow-hidden border border-white/5 hover:border-primary/30 transition-all hover:shadow-2xl hover:shadow-primary/5">
                    <div class="aspect-video overflow-hidden">
                        <img v-if="project.image" :src="project.image" :alt="project.title"
                            class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
                        <div v-else
                            class="w-full h-full bg-gradient-to-br from-primary/20 to-secondary/20 flex items-center justify-center">
                            <div
                                class="text-white/20 font-bold text-4xl group-hover:scale-110 transition-transform duration-500">
                                {{ project.title[0] }}</div>
                        </div>
                    </div>

                    <div class="p-8">
                        <span class="text-xs font-bold text-primary uppercase tracking-widest mb-2 block">{{
                            project.category }}</span>
                        <h3 class="text-xl font-bold mb-4">{{ project.title }}</h3>
                        <p class="text-gray-400 text-sm mb-6 line-clamp-2">{{ project.desc }}</p>

                        <div class="flex flex-wrap gap-2">
                            <span v-for="tag in project.tags" :key="tag"
                                class="text-[10px] bg-white/5 text-gray-400 px-3 py-1 rounded-full border border-white/10 uppercase tracking-tighter">
                                {{ tag }}
                            </span>
                        </div>
                    </div>

                    <!-- Hover reveal link -->
                    <div
                        class="absolute inset-0 bg-primary/90 opacity-0 group-hover:opacity-100 transition-opacity flex flex-col items-center justify-center p-8 text-center cursor-pointer">
                        <h3 class="text-2xl font-bold text-dark mb-4">{{ project.title }}</h3>
                        <p class="text-dark/80 mb-6 font-medium">View detailed case study of this project.</p>
                        <div class="w-12 h-12 bg-dark rounded-full flex items-center justify-center">
                            <span class="text-primary text-2xl font-bold">→</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const tabs = ['All', 'UI/UX Design', 'Web Dev', 'Branding']
const activeTab = ref('All')

const projects = [
    { id: 1, title: 'E-Commerce Platform', category: 'Web Dev', desc: 'A full-featured shopping experience with real-time inventory.', tags: ['Vue 3', 'Node.js', 'PostgreSQL'], image: '/assets/project1.png' },
    { id: 2, title: 'Fitness Tracker App', category: 'UI/UX Design', desc: 'Modern interface for tracking daily activities and health goals.', tags: ['Figma', 'Prototyping'], image: '/assets/project2.png' },
    { id: 3, title: 'Brand Identity Design', category: 'Branding', desc: 'Developing a unique visual language for a tech startup.', tags: ['Identity', 'Guidelines'], image: '/assets/project3.png' },
    { id: 4, title: 'Real Estate Portal', category: 'Web Dev', desc: 'Interactive property searching and virtual tours.', tags: ['Vite', 'Firebase'], image: '/assets/project4.png' },
    { id: 5, title: 'Food Delivery App', category: 'UI/UX Design', desc: 'Streamlined UX for ordering and real-time delivery tracking.', tags: ['Mobile Design', 'UI Kit'], image: '/assets/project2.png' },
    { id: 6, title: 'Dashboard UI', category: 'UI/UX Design', desc: 'Complex data visualization and management system.', tags: ['React', 'Charts'], image: '/assets/project1.png' },
]

const filteredProjects = computed(() => {
    if (activeTab.value === 'All') return projects
    return projects.filter(p => p.category === activeTab.value)
})
</script>
