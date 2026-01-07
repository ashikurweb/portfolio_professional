<template>
    <section id="about" ref="aboutRef" class="relative bg-[#020408] text-white py-0 overflow-hidden">
        <!-- Section 1: The Narrative Intro -->
        <div
            class="min-h-screen relative flex items-center justify-center pt-20 pb-40 px-6 sm:px-12 lg:px-24 overflow-hidden manifesto-container">
            <!-- Dynamic Background Glows -->
            <div
                class="absolute top-1/4 -left-20 w-[600px] h-[600px] bg-primary/5 blur-[120px] rounded-full pointer-events-none animate-pulse bg-focal">
            </div>
            <div
                class="absolute bottom-1/4 -right-20 w-[400px] h-[400px] bg-primary/5 blur-[150px] rounded-full pointer-events-none">
            </div>

            <div class="max-w-7xl w-full relative z-10">
                <div class="grid lg:grid-cols-[1.3fr_1fr] gap-20 items-center">
                    <div class="space-y-12">
                        <div class="space-y-6">
                            <div class="flex items-center gap-4 manifesto-reveal opacity-0 -translate-y-10">
                                <div class="w-12 h-[1px] bg-primary/30"></div>
                                <span
                                    class="text-[10px] font-black tracking-[0.5em] uppercase text-primary italic">System_User:
                                    Ashikur_Rahman_v4.1</span>
                            </div>

                            <h2
                                class="text-7xl md:text-[11rem] font-black leading-[0.8] tracking-tighter uppercase relative">
                                <div class="overflow-hidden pb-4">
                                    <span class="block m-line translate-y-full">CODE_IS</span>
                                </div>
                                <div class="overflow-hidden">
                                    <span class="block m-line translate-y-full italic text-primary">ARCHITECTURE</span>
                                </div>
                            </h2>
                        </div>

                        <!-- Summary Bio -->
                        <div class="max-w-2xl manifesto-reveal opacity-0 translate-y-10">
                            <p
                                class="text-3xl md:text-5xl font-bold leading-[1.2] text-white/40 tracking-tight bio-text-reveal">
                                I am a <span class="text-white">Software Engineer</span> at Codeshaper, specializing in
                                <span class="text-white italic">modern web applications</span> and backend architecture.
                            </p>
                        </div>
                    </div>

                    <!-- Right: Quick Facts Hub -->
                    <div class="manifesto-reveal opacity-0 translate-x-10 hidden lg:block">
                        <div
                            class="p-12 bg-white/[0.02] border border-white/5 rounded-[4rem] backdrop-blur-3xl space-y-10 group hover:border-primary/20 transition-all duration-1000">
                            <div class="space-y-2">
                                <h4 class="text-[10px] font-black text-primary uppercase tracking-[0.4em] mb-10">//
                                    QUICK_FACTS_PROFILE</h4>
                                <div class="space-y-5 text-sm">
                                    <div v-for="fact in quickFacts" :key="fact.label"
                                        class="flex items-center gap-4 border-b border-white/5 pb-4 last:border-0">
                                        <component :is="fact.icon" size="16" class="text-primary/60" />
                                        <div class="flex flex-col">
                                            <span class="text-[9px] text-white/20 uppercase tracking-widest">{{
                                                fact.label }}</span>
                                            <span class="font-bold text-white/90">{{ fact.value }}</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div
                                class="pt-2 flex items-center justify-between text-white/10 text-[9px] font-mono tracking-widest uppercase">
                                <span class="flex items-center gap-2 animate-pulse">
                                    <div class="w-1.5 h-1.5 rounded-full bg-primary"></div> STATUS: OPTIMIZING
                                </span>
                                <span>v4.1.0</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div
                class="absolute bottom-10 left-10 md:left-24 rotate-[-90deg] origin-left text-[10px] font-mono tracking-[0.5em] text-white/10 uppercase italic hidden sm:block">
                SCROLL_TO_ACCESS_SYSTEM_DATA
            </div>
        </div>

        <!-- Section 2: Core Pillars -->
        <div class="py-40 bg-[#05070A] border-y border-white/5 relative overflow-hidden">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 text-center mb-24">
                <span class="text-primary font-mono text-[10px] tracking-[0.4em] uppercase mb-4 block">01.
                    PHILOSOPHY_NODES</span>
                <h3 class="text-4xl md:text-6xl font-black italic uppercase italic">CORE <span
                        class="text-primary">PRINCIPLES</span></h3>
            </div>
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
                    <div v-for="(pillar, index) in pillars" :key="index" @mousemove="handleCardMove($event, index)"
                        @mouseleave="handleCardLeave(index)" ref="cardRefs"
                        class="pillar-card group relative p-12 rounded-[2.5rem] bg-[#0A0F1E]/50 border border-white/5 overflow-hidden backdrop-blur-sm transition-colors duration-500 hover:border-primary/30"
                        style="perspective: 1000px;">
                        <div class="card-spotlight absolute inset-0 bg-radial-gradient from-primary/10 to-transparent opacity-0 transition-opacity duration-500 pointer-events-none"
                            :style="spotlightStyle[index]"></div>
                        <div class="relative z-10 space-y-8 pillar-content">
                            <div
                                class="w-20 h-20 rounded-2xl bg-white/5 flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-dark transition-all duration-700 p-icon">
                                <component :is="pillar.icon" size="40" stroke-width="1.5" />
                            </div>
                            <div class="space-y-4">
                                <h3 class="text-3xl font-black uppercase italic leading-none tracking-tighter">{{
                                    pillar.title }}</h3>
                                <p
                                    class="text-white/30 group-hover:text-white/60 transition-colors duration-700 leading-relaxed font-medium text-base">
                                    {{ pillar.desc }}</p>
                            </div>
                            <div
                                class="pt-6 flex justify-between items-end border-t border-white/5 group-hover:border-primary/20 transition-colors duration-700">
                                <span
                                    class="text-5xl font-black text-white/[0.04] group-hover:text-primary transition-all duration-700 italic leading-none">0{{
                                        index + 1 }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Section 3: The Creative Protocol -->
        <div class="py-40 relative overflow-hidden bg-[#020408]">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="mb-24 flex flex-col lg:flex-row lg:items-end justify-between gap-8">
                    <div class="space-y-4">
                        <span
                            class="text-primary font-mono font-black uppercase tracking-[0.5em] text-[10px] block animate-pulse">02.
                            OPERATIONAL_FLOW</span>
                        <h3 class="text-5xl md:text-[7rem] font-black italic uppercase leading-none tracking-tighter">
                            CREATIVE <span class="text-primary">PROTOCOL</span></h3>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div v-for="(step, index) in process" :key="index" class="protocol-step group relative">
                        <div
                            class="relative z-10 p-10 rounded-[3rem] bg-white/[0.02] border border-white/5 group-hover:border-primary/30 transition-all duration-700 h-full backdrop-blur-xl flex flex-col justify-between overflow-hidden">
                            <div
                                class="absolute -right-4 -bottom-4 w-24 h-24 bg-primary/5 blur-2xl rounded-full opacity-0 group-hover:opacity-100 transition-opacity">
                            </div>
                            <div class="space-y-6 relative z-10">
                                <div
                                    class="w-16 h-16 rounded-2xl bg-white/5 flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-dark transition-all duration-700 shadow-2xl">
                                    <component :is="step.icon" size="30" stroke-width="1.5" />
                                </div>
                                <div class="space-y-4">
                                    <div class="flex items-center gap-3">
                                        <span class="text-[10px] font-mono text-primary/40 uppercase">Phase_0{{ index +
                                            1 }}</span>
                                    </div>
                                    <h4 class="text-2xl font-black uppercase italic tracking-tighter">{{ step.title }}
                                    </h4>
                                    <p
                                        class="text-sm text-white/40 leading-relaxed group-hover:text-white/60 transition-colors">
                                        {{ step.desc }}</p>
                                </div>
                            </div>
                            <div class="mt-8 h-1 w-full bg-white/5 rounded-full overflow-hidden">
                                <div
                                    class="h-full bg-primary scale-x-0 group-hover:scale-x-100 transition-transform duration-1000 origin-left">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Section 4: The Career Matrix (Previous Card Design) -->
        <div class="py-40 relative bg-[#05070A] border-y border-white/5">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="mb-32 text-center">
                    <span class="text-primary font-mono text-[10px] tracking-[0.4em] uppercase mb-4 block">03.
                        SYSTEM_GENESIS</span>
                    <h3 class="text-5xl md:text-8xl font-black italic uppercase tracking-tighter">ELITE <br /> <span
                            class="text-primary tracking-normal">EXPERIENCE</span></h3>
                </div>

                <div class="space-y-40">
                    <!-- Professional Experience -->
                    <div class="space-y-12">
                        <div class="flex items-center gap-6 mb-16">
                            <div class="p-4 bg-primary/10 border border-primary/20 rounded-2xl text-primary">
                                <BriefcaseIcon size="32" />
                            </div>
                            <h4 class="text-3xl font-black uppercase italic tracking-widest">MASTER_PROTOCOL</h4>
                        </div>

                        <div class="grid grid-cols-1 gap-8">
                            <div v-for="(exp, index) in experience" :key="index"
                                class="exp-card p-12 bg-white/[0.02] border border-white/5 rounded-[4rem] hover:border-primary/30 transition-all duration-1000 group relative overflow-hidden backdrop-blur-3xl">
                                <div
                                    class="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity">
                                </div>
                                <div
                                    class="flex flex-col lg:flex-row lg:items-center justify-between gap-12 relative z-10">
                                    <div class="flex items-center gap-10">
                                        <div
                                            class="w-32 h-32 rounded-[3rem] bg-white/5 flex flex-col items-center justify-center border border-white/10 group-hover:bg-primary group-hover:text-dark transition-all duration-700">
                                            <span class="text-xs font-black opacity-40 uppercase">Year</span>
                                            <span class="text-2xl font-black italic">{{ exp.period.includes('Present') ?
                                                '2024' : exp.period.split(' - ')[0] }}</span>
                                        </div>
                                        <div class="space-y-2">
                                            <h5
                                                class="text-4xl md:text-6xl font-black italic uppercase text-primary leading-tight">
                                                {{ exp.role }}</h5>
                                            <p class="text-white/40 font-bold tracking-widest text-xs uppercase">{{
                                                exp.company }} | {{ exp.period }}</p>
                                        </div>
                                    </div>
                                    <div class="flex-1 lg:max-w-2xl">
                                        <ul class="grid grid-cols-1 md:grid-cols-2 gap-x-12 gap-y-4">
                                            <li v-for="(point, pIdx) in exp.points" :key="pIdx"
                                                class="flex gap-4 text-sm text-white/40 leading-relaxed group-hover:text-white/60">
                                                <span class="text-primary mt-1.5 font-bold">»</span>
                                                {{ point }}
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Academic History -->
                    <div class="space-y-12">
                        <div class="flex items-center gap-6 mb-16">
                            <div class="p-4 bg-primary/10 border border-primary/20 rounded-2xl text-primary">
                                <GraduationCapIcon size="32" />
                            </div>
                            <h4 class="text-3xl font-black uppercase italic tracking-widest">ACADEMIC_ARC</h4>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                            <div v-for="(edu, index) in education" :key="index"
                                class="edu-card p-10 bg-white/[0.02] border border-white/5 rounded-[3rem] hover:border-primary/30 transition-all duration-700 group relative overflow-hidden">
                                <div
                                    class="absolute top-0 right-0 p-8 opacity-[0.03] group-hover:opacity-10 transition-opacity">
                                    <GraduationCapIcon size="120" />
                                </div>
                                <div class="space-y-6 relative z-10">
                                    <div class="space-y-1">
                                        <span
                                            class="text-[10px] font-mono text-primary/60 tracking-[0.4em] uppercase">{{
                                                edu.period }}</span>
                                        <h5 class="text-3xl font-black uppercase italic leading-tight">{{ edu.title }}
                                        </h5>
                                    </div>
                                    <div class="p-6 bg-white/[0.03] border border-white/5 rounded-2xl">
                                        <p class="text-sm font-bold text-white/60 mb-1">{{ edu.institution }}</p>
                                        <p class="text-[10px] text-white/30 uppercase tracking-widest">{{ edu.location
                                        }}</p>
                                    </div>
                                    <p class="text-sm text-white/40 leading-relaxed italic pr-4">{{ edu.desc }}</p>
                                    <div class="pt-4 border-t border-white/5 flex items-center justify-between">
                                        <span
                                            class="text-[10px] font-black text-primary uppercase tracking-widest">Grade_Index</span>
                                        <span class="text-3xl font-black italic">{{ edu.grade }}</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Section 5: Detailed Bio -->
        <div class="py-40 bg-[#0A0F1E] relative overflow-hidden">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="grid lg:grid-cols-2 gap-32 items-center">
                    <div class="space-y-12 bio-content">
                        <div class="space-y-8">
                            <div class="h-[1px] w-20 bg-primary"></div>
                            <h4 class="text-5xl md:text-[5.5rem] font-black uppercase italic leading-[0.9]">Architecting
                                <br /> <span class="text-primary italic">Interfaces</span> With Precision
                            </h4>
                            <p class="text-white/60 text-2xl leading-relaxed italic pr-10">"Strategic, goal-oriented,
                                and obsessed with the intersection of performance and high-end aesthetic."</p>
                            <p class="text-white/40 leading-relaxed text-lg">
                                Enthusiastic Software Engineer focusing on backend stability and frontend fluidity.
                                Experience in building scalable ecosystems and modern user experiences.
                            </p>
                        </div>
                        <div
                            class="p-10 bg-white/[0.02] border border-white/5 rounded-[3rem] backdrop-blur-2xl grid grid-cols-2 gap-10 relative overflow-hidden group">
                            <div class="absolute top-0 right-0 p-4 opacity-5 group-hover:opacity-20 transition-opacity">
                                <TerminalIcon size="100" />
                            </div>
                            <div v-for="info in personalInfo" :key="info.label"><span
                                    class="text-[10px] text-primary font-mono uppercase tracking-[0.3em] block mb-2 opacity-60">{{
                                        info.label }}</span><span class="text-base font-bold text-white/90">{{ info.value
                                    }}</span></div>
                        </div>
                    </div>
                    <div class="relative bio-visual">
                        <div class="relative aspect-square max-w-[500px] mx-auto group">
                            <div
                                class="absolute inset-0 border-[40px] border-white/5 rounded-[4rem] group-hover:rotate-12 transition-transform duration-1000">
                            </div>
                            <div class="absolute inset-4 border border-primary/20 rounded-[3rem] animate-pulse"></div>
                            <div class="relative w-full h-full rounded-[3.5rem] overflow-hidden shadow-2xl"><img
                                    src="/assets/about.png" alt="Ashikur Rahman"
                                    class="w-full h-full object-cover grayscale brightness-75 group-hover:grayscale-0 group-hover:brightness-100 transition-all duration-1000 scale-110 group-hover:scale-100" />
                                <div
                                    class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-60">
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
import { onMounted, ref, reactive } from 'vue'
import {
    Code2Icon, SparklesIcon, TargetIcon, SearchIcon, LayersIcon, ShieldCheckIcon, TerminalIcon, BriefcaseIcon, GraduationCapIcon, ZapIcon, CpuIcon, RocketIcon, ActivityIcon, Building2Icon, MapPinIcon, LaptopIcon, PaletteIcon, LeafIcon, SwordsIcon, TargetIcon as GoalIcon
} from 'lucide-vue-next'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const aboutRef = ref(null)
const cardRefs = ref([])
const spotlightStyle = reactive({})

const pillars = [
    { title: 'Modern Logic', desc: 'Crafting error-free websites with human-readable, highly efficient codebase logic.', icon: Code2Icon },
    { title: 'Tactical Precision', desc: 'Operating with an end-goal mindset to ensure every pixel serves a tactical mission.', icon: TargetIcon },
    { title: 'Fluid Aesthetic', desc: 'A relentless obsession with sub-pixel precision and 100% user satisfaction.', icon: SparklesIcon },
]

const process = [
    { title: 'Discovery_Map', desc: 'Establishing technical scope and mission architecture through data mapping.', icon: SearchIcon },
    { title: 'Logic_DNA', desc: 'Building the fundamental structure of the application with optimized logic.', icon: LayersIcon },
    { title: 'Nexus_Core', desc: 'Engineering high-fidelity UIs using React.js and modern JavaScript.', icon: Code2Icon },
    { title: 'Sanity_Check', desc: 'Rigorous protocol testing to ensure absolute visual and functional stability.', icon: ShieldCheckIcon },
    { title: 'Perf_Sync', desc: 'Integrating high-speed optimizations for sub-second loading performance.', icon: ZapIcon },
    { title: 'Scale_Audit', desc: 'Architecting for modularity to ensure horizontal scaling of infrastructure.', icon: CpuIcon },
    { title: 'Deployment', desc: 'Securely pushing artifacts to production via automated CI/CD pipelines.', icon: RocketIcon },
    { title: 'Evolution_Loop', desc: 'Continuous loop monitoring and feedback-driven refinement for longevity.', icon: ActivityIcon },
]

const quickFacts = [
    { label: 'ROLE', value: 'Software Engineer @ CodeShaper', icon: Building2Icon },
    { label: 'BASE', value: 'Dhaka, Bangladesh', icon: MapPinIcon },
    { label: 'TECH', value: '1 Year Experience', icon: LaptopIcon },
    { label: 'PASSION', value: 'Clean Code & Modern Design', icon: PaletteIcon },
    { label: 'GROWTH', value: 'Mastering React.js & JS', icon: LeafIcon },
    { label: 'SKILL', value: 'Solving Complex Problems', icon: SwordsIcon },
    { label: 'MISSION', value: 'Impactful Applications', icon: GoalIcon },
]

const experience = [
    {
        role: 'Software Engineer',
        company: 'Codeshaper',
        period: '2024 - Present',
        tags: ['Laravel', 'React', 'Arch', 'Logic'],
        points: ['Modern web application development.', 'PHP (Laravel) backend architecture.', 'Scalable database structure design.', 'API optimization and integration.']
    }
]

const education = [
    { title: 'Diploma in Computer Science', institution: 'Pabna Polytechnic Institute', location: 'Pabna, Bangladesh', period: '2019 - 2023', grade: 'CGPA 3.58', desc: 'Technical mastery of software engineering principles.' },
    { title: 'Secondary School Certificate', institution: 'SaratGonj T.A High School', location: 'Chatmohar, Pabna', period: '2018 - 2019', grade: 'GPA 4.39', desc: 'Significant academic standing in science and math.' }
]

const personalInfo = [
    { label: 'RESIDENCE', value: 'Dhaka, Bangladesh' },
    { label: 'TEMPORAL', value: '31 Oct 2003 (21y)' },
    { label: 'ACADEMIC', value: 'Diploma in CSE' },
    { label: 'EMAIL', value: 'ashikurrahman7194@gmail.com' },
    { label: 'CONTACT', value: '+8801700-917194' },
    { label: 'STATUS', value: 'Available for Excellence' },
]

const handleCardMove = (e, index) => {
    const card = cardRefs.value[index]; if (!card) return;
    const rect = card.getBoundingClientRect(); const x = e.clientX - rect.left; const y = e.clientY - rect.top;
    spotlightStyle[index] = { background: `radial-gradient(400px circle at ${x}px ${y}px, rgba(0, 210, 123, 0.15), transparent 80%)`, opacity: 1 }
    const centerY = rect.height / 2; const rotateX = (centerY - y) / 12; const centerX = rect.width / 2; const rotateY = (x - centerX) / 12;
    gsap.to(card, { rotateX, rotateY, duration: 0.5, ease: 'power2.out' })
}

const handleCardLeave = (index) => {
    const card = cardRefs.value[index]; if (!card) return;
    spotlightStyle[index] = { opacity: 0 }; gsap.to(card, { rotateX: 0, rotateY: 0, duration: 0.8, ease: 'elastic.out(1, 0.3)' })
}

onMounted(() => {
    const ctx = gsap.context(() => {
        gsap.to('.m-line', { y: 0, duration: 2, ease: 'expo.out', stagger: 0.3, delay: 0.5 })
        gsap.to('.manifesto-reveal', { opacity: 1, y: 0, duration: 1.5, stagger: 0.2, delay: 1.2, ease: 'power3.out' })
        gsap.to('.m-line', { scrollTrigger: { trigger: '.manifesto-container', start: 'top top', end: 'bottom top', scrub: 1 }, y: -150, stagger: 0.05 })
        gsap.to('.bg-focal', { scrollTrigger: { trigger: '#about', start: 'top bottom', end: 'bottom top', scrub: 2 }, y: 300, scale: 1.2 })

        // Creative Protocol: Side-Curve
        gsap.from('.protocol-step', {
            scrollTrigger: { trigger: '.protocol-step', start: 'top 85%', end: 'top 30%', scrub: 1.2 },
            opacity: 0, scale: 0.4, x: (i) => (i % 2 === 0 ? -400 : 400), y: 200, rotation: (i) => (i % 2 === 0 ? -20 : 20), stagger: 0.1, ease: 'expo.out'
        })

        // Career Matrix: High-Performance Swings
        const items = gsap.utils.toArray('.exp-card, .edu-card')
        items.forEach((item, i) => {
            gsap.from(item, {
                scrollTrigger: { trigger: item, start: 'top 90%', end: 'top 50%', scrub: 1 },
                opacity: 0, x: i % 2 === 0 ? -150 : 150, rotation: i % 2 === 0 ? -5 : 5, ease: 'power2.out'
            })
        })

        gsap.from('.bio-content', { scrollTrigger: { trigger: '.bio-content', start: 'top 85%', end: 'top 30%', scrub: 1 }, x: -50, opacity: 0, ease: 'power2.out' })
        gsap.from('.bio-visual', { scrollTrigger: { trigger: '.bio-content', start: 'top 85%', end: 'top 30%', scrub: 1.5 }, scale: 0.9, opacity: 0.2, y: 100, ease: 'power3.out' })
    }, aboutRef.value)
})
</script>

<style scoped>
.m-line {
    transform: translateY(100%);
}
</style>
