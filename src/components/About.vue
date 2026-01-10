<template>
    <section id="about" ref="aboutRef" class="relative bg-[#020408] text-white py-0 overflow-hidden">
        <!-- Section 1: The Technical Architect DNA (New Strategic Intro) -->


        <!-- Section 2: Core Pillars -->
        <div class="py-40 bg-[#05070A] border-y border-white/5 relative overflow-hidden">
            <div
                class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 text-center mb-24 pillar-header overflow-hidden">
                <!-- Parallax Background Stroke Text -->
                <div class="absolute inset-0 flex items-center justify-center pointer-events-none -z-10 opacity-[0.03]">
                    <span
                        class="text-[15rem] font-black italic uppercase outline-text-v2 pillar-bg-text">FOUNDATION</span>
                </div>

                <div class="pillar-label opacity-0 -translate-y-4">
                    <span
                        class="text-primary font-mono text-[10px] tracking-[0.6em] uppercase mb-6 block animate-pulse">//
                        SYSTEM_PILLARS_v1.0</span>
                </div>

                <h3
                    class="text-3xl sm:text-5xl md:text-[8rem] font-black italic uppercase leading-none tracking-tighter relative">
                    <div class="overflow-hidden flex justify-center">
                        <span class="block pillar-slide-text opacity-0 -translate-x-full">CORE</span>
                        <span
                            class="block text-primary pillar-slide-text opacity-0 translate-x-full ml-[0.2em] s-glitch"
                            data-text="PRINCIPLES">PRINCIPLES</span>
                    </div>
                    <!-- Technical Accent -->
                    <div class="mt-4 flex items-center justify-center gap-4 pillar-accent opacity-0 translate-y-4">
                        <div class="w-12 h-[1px] bg-primary/30"></div>
                        <span class="text-[9px] font-mono text-white/20 tracking-[1em]">NON_NEGOTIABLE_PROTOCOLS</span>
                        <div class="w-12 h-[1px] bg-primary/30"></div>
                    </div>
                </h3>
            </div>
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-10 pillar-grid">
                    <div v-for="(pillar, index) in pillars" :key="index" @mousemove="handleCardMove($event, index)"
                        @mouseleave="handleCardLeave(index)" ref="cardRefs"
                        class="pillar-card group relative p-6 sm:p-10 rounded-[2.5rem] sm:rounded-[4rem] bg-[#0A0F1E]/40 border border-white/10 overflow-hidden backdrop-blur-2xl transition-all duration-700 hover:border-primary/40"
                        style="perspective: 1500px;">

                        <!-- Internal Grid Pattern -->
                        <div
                            class="absolute inset-0 opacity-[0.03] group-hover:opacity-[0.07] transition-opacity pointer-events-none bg-[radial-gradient(#ffffff_1px,transparent_1px)] bg-[size:20px_20px]">
                        </div>

                        <!-- Hover Spotlight (Kept as requested) -->
                        <div class="card-spotlight absolute inset-0 bg-radial-gradient from-primary/10 to-transparent opacity-0 transition-opacity duration-500 pointer-events-none"
                            :style="spotlightStyle[index]"></div>

                        <div class="relative z-10 h-full flex flex-col justify-between pillar-content">
                            <!-- Top Data Strip -->
                            <div class="flex items-center justify-between mb-12">
                                <div class="flex items-center gap-3">
                                    <div class="w-2 h-2 rounded-full bg-primary animate-pulse"></div>
                                    <span class="text-[9px] font-mono text-white/40 tracking-[0.3em]">PILLAR_NODE_0{{
                                        index + 1 }}</span>
                                </div>
                                <div class="w-10 h-[1px] bg-white/10"></div>
                            </div>

                            <div class="space-y-10">
                                <!-- Holographic Icon Base -->
                                <div class="relative w-20 h-20 p-icon">
                                    <div
                                        class="absolute inset-0 bg-primary/20 blur-2xl rounded-full scale-0 group-hover:scale-150 transition-transform duration-1000 opacity-0 group-hover:opacity-100">
                                    </div>
                                    <div
                                        class="relative w-full h-full rounded-2xl bg-white/[0.03] border border-white/10 flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-dark transition-all duration-700 shadow-2xl z-10">
                                        <component :is="pillar.icon" size="36" stroke-width="1.2" />
                                    </div>
                                    <!-- Base Line Accent -->
                                    <div
                                        class="absolute -bottom-2 left-1/2 -translate-x-1/2 w-12 h-[2px] bg-primary/30 rounded-full blur-[1px]">
                                    </div>
                                </div>

                                <div class="space-y-4">
                                    <h3
                                        class="text-3xl font-black uppercase italic leading-none tracking-tighter group-hover:text-primary transition-colors duration-500">
                                        {{ pillar.title }}
                                    </h3>
                                    <p
                                        class="text-white/40 group-hover:text-white/70 transition-colors duration-700 leading-relaxed font-medium text-sm italic pr-4">
                                        {{ pillar.desc }}
                                    </p>
                                </div>
                            </div>

                            <!-- Bottom Terminal Label -->
                            <div
                                class="mt-12 pt-6 border-t border-white/5 flex justify-between items-center group-hover:border-primary/20 transition-colors duration-700">
                                <span class="text-[9px] font-mono text-white/20 uppercase tracking-widest">STATUS:
                                    OPTIMIZED</span>
                                <span
                                    class="text-4xl font-black text-white/[0.03] group-hover:text-primary/10 transition-all duration-700 italic leading-none">#0{{
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
                <div class="mb-24 protocol-header overflow-hidden">
                    <div class="protocol-label opacity-0 -translate-x-10">
                        <span
                            class="text-primary font-mono font-black uppercase tracking-[0.5em] text-[10px] block animate-pulse">02.
                            OPERATIONAL_FLOW</span>
                    </div>
                    <h3
                        class="text-3xl sm:text-5xl md:text-[7rem] font-black italic uppercase leading-none tracking-tighter">
                        <div class="overflow-hidden">
                            <span class="block protocol-slide-text opacity-0 -translate-x-full">CREATIVE</span>
                        </div>
                        <div class="overflow-hidden">
                            <span
                                class="block text-primary protocol-slide-text opacity-0 translate-x-full">PROTOCOL</span>
                        </div>
                    </h3>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div v-for="(step, index) in process" :key="index" class="protocol-step group relative">
                        <div
                            class="relative z-10 p-6 sm:p-10 rounded-[2rem] sm:rounded-[3rem] bg-white/[0.02] border border-white/5 group-hover:border-primary/30 transition-all duration-700 h-full backdrop-blur-xl flex flex-col justify-between overflow-hidden">
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

        <!-- Section 4: The Elite Stream (High-Performance Kinetic Timeline) -->
        <div class="py-60 relative bg-[#020408] overflow-hidden stream-section">
            <!-- Background Parallax Text -->
            <div
                class="absolute inset-0 flex items-center justify-center opacity-[0.03] pointer-events-none select-none stream-bg-text">
                <span class="text-[35vw] font-black italic uppercase tracking-tighter succession-text">SUCCESSION</span>
            </div>

            <!-- Technical Scanning Grid -->
            <div
                class="absolute inset-0 bg-[linear-gradient(to_right,#ffffff03_1px,transparent_1px),linear-gradient(to_bottom,#ffffff03_1px,transparent_1px)] bg-[size:40px_40px] [mask-image:radial-gradient(ellipse_60%_50%_at_50%_0%,#000_70%,transparent_100%)]">
            </div>

            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="mb-40 stream-header overflow-hidden">
                    <div class="stream-label opacity-0 -translate-x-10">
                        <span
                            class="text-primary font-mono text-[10px] tracking-[0.5em] uppercase mb-4 block animate-pulse">//
                            SYSTEM_GENESIS_v2.0</span>
                    </div>

                    <h3
                        class="text-4xl sm:text-6xl md:text-[11rem] font-black italic uppercase tracking-tighter leading-[0.85] relative">
                        <div class="overflow-hidden">
                            <span class="block text-white stream-slide-text opacity-0 -translate-x-full">ELITE</span>
                        </div>
                        <div class="overflow-hidden">
                            <span
                                class="block text-primary ml-[0.1em] s-glitch stream-slide-text opacity-0 translate-x-full"
                                data-text="EXPERIENCE">EXPERIENCE</span>
                        </div>
                        <div
                            class="absolute -right-10 top-0 text-[10px] font-mono text-white/10 rotate-90 origin-left tracking-[1em] hidden lg:block header-tag opacity-0">
                            SYSTEM_ARCH_v4.1
                        </div>
                    </h3>
                </div>

                <!-- Personal Identity Matrix (New Addition) -->
                <!-- Personal Identity Matrix (High-Tech HUD Design) -->
                <div class="mb-32 relative z-10 w-full overflow-hidden">
                    <div
                        class="flex flex-wrap gap-4 justify-center lg:justify-between p-8 rounded-[2rem] bg-white/[0.01] border border-white/5 backdrop-blur-md relative group/hud">

                        <!-- HUD Scanline (Moving) -->
                        <div
                            class="absolute top-0 left-0 w-full h-[1px] bg-gradient-to-r from-transparent via-primary/30 to-transparent translate-y-0 opacity-0 group-hover/hud:opacity-100 group-hover/hud:translate-y-[200px] transition-all duration-[3s] ease-linear">
                        </div>

                        <div v-for="(info, i) in personalInfo" :key="i"
                            class="personal-card relative group/card flex-1 min-w-[200px] p-6 rounded-xl bg-white/[0.02] border border-white/5 hover:bg-white/[0.04] hover:border-primary/20 transition-all duration-500 overflow-hidden cursor-default opacity-0">

                            <div class="flex flex-col h-full justify-between gap-4 relative z-10">
                                <!-- Icon (Appears on Hover) -->
                                <div
                                    class="absolute -right-2 -top-2 text-primary/10 group-hover/card:text-primary/20 transform group-hover/card:scale-110 group-hover/card:rotate-12 transition-all duration-700">
                                    <component :is="info.icon" size="60" stroke-width="1" />
                                </div>

                                <div class="flex items-center gap-3">
                                    <component :is="info.icon" size="16"
                                        class="text-primary/60 group-hover/card:text-primary transition-colors" />
                                    <span
                                        class="text-[9px] font-mono text-white/30 uppercase tracking-[0.2em] group-hover/card:text-primary/70 transition-colors">{{
                                            info.label }}</span>
                                </div>

                                <div>
                                    <span
                                        class="block text-sm font-bold text-white/90 leading-snug group-hover/card:text-white transition-colors font-sans break-words">{{
                                            info.value }}</span>
                                </div>
                            </div>

                            <!-- Active Status Dot -->
                            <div
                                class="absolute bottom-3 right-3 w-1.5 h-1.5 rounded-full bg-white/10 group-hover/card:bg-primary group-hover/card:shadow-[0_0_10px_#00d27b] transition-all duration-500">
                            </div>
                        </div>

                    </div>

                    <!-- System Decoration Line -->
                    <div
                        class="flex items-center justify-between text-[9px] font-mono text-white/10 px-4 mt-2 uppercase tracking-widest">
                        <span>/// SYS.ID_MATRIX_LOADED</span>
                        <span>[SECURE_CONNECTION]</span>
                    </div>
                </div>

                <!-- The Stream Container -->
                <div class="relative">
                    <!-- Central Conduit (Data Line) -->
                    <div
                        class="absolute left-0 md:left-1/2 top-0 bottom-0 w-[2px] bg-white/5 -translate-x-1/2 hidden md:block conduit-line overflow-hidden">
                        <div
                            class="absolute top-0 left-0 w-full bg-primary conduit-progress origin-top h-full scale-y-0">
                        </div>
                    </div>

                    <div class="space-y-60">
                        <!-- Professional Peak -->
                        <div v-for="(exp, index) in experience" :key="'exp-' + index"
                            class="stream-item relative grid md:grid-cols-2 gap-10 md:gap-32">
                            <!-- Left: Label/Metadata -->
                            <div class="flex items-center md:justify-end md:text-right order-1">
                                <div class="space-y-4 stream-meta">
                                    <div class="flex items-center gap-4 md:flex-row-reverse">
                                        <div class="w-12 h-[1px] bg-primary"></div>
                                        <span
                                            class="text-xs font-mono text-primary uppercase tracking-[0.4em]">MASTER_PROTOCOL_0{{
                                                index + 1 }}</span>
                                    </div>
                                    <div class="relative group/year">
                                        <!-- Technical Corner Markers -->
                                        <div
                                            class="absolute -top-4 -left-4 w-4 h-4 border-t-2 border-l-2 border-primary/30 group-hover/year:border-primary transition-colors">
                                        </div>
                                        <div
                                            class="absolute -bottom-4 -right-4 w-4 h-4 border-b-2 border-r-2 border-primary/30 group-hover/year:border-primary transition-colors">
                                        </div>

                                        <div
                                            class="relative overflow-hidden bg-white/[0.02] border border-white/10 rounded-2xl p-4 sm:p-8 backdrop-blur-xl group-hover/year:border-primary/50 transition-all duration-700">
                                            <div
                                                class="absolute top-0 left-0 w-full h-[1px] bg-gradient-to-r from-transparent via-primary/50 to-transparent -translate-x-full group-hover/year:translate-x-full transition-transform duration-1000">
                                            </div>

                                            <h4
                                                class="text-5xl sm:text-7xl md:text-9xl font-black italic leading-none outline-text-v2 uppercase">
                                                {{ exp.period.includes('Present') ? '2024' : exp.period.split(' - ')[0]
                                                }}
                                            </h4>

                                            <div
                                                class="mt-4 flex items-center justify-between text-[10px] font-mono tracking-widest text-primary/40">
                                                <span>STATUS: ACTIVE</span>
                                                <span>NODE_ID: {{ index + 1 }}</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <!-- Right: Detailed Content -->
                            <div class="stream-content order-2 self-center">
                                <div class="space-y-8">
                                    <h5
                                        class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-black italic uppercase leading-tight">
                                        {{ exp.role }} <br />
                                        <span class="text-primary">{{ exp.company }}</span>
                                    </h5>
                                    <div
                                        class="flex items-center gap-6 text-white/40 font-mono text-xs tracking-widest">
                                        <span class="px-3 py-1 bg-white/5 rounded-full border border-white/10 italic">{{
                                            exp.period }}</span>
                                        <span class="flex items-center gap-2">
                                            <div class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse"></div>
                                            LATEST_DEPLOYMENT
                                        </span>
                                    </div>
                                    <ul class="space-y-6 max-w-lg">
                                        <li v-for="(point, pIdx) in exp.points" :key="pIdx"
                                            class="group flex gap-6 text-base text-white/40 leading-relaxed hover:text-white/80 transition-colors duration-500">
                                            <span
                                                class="text-primary font-black mt-1 group-hover:translate-x-1 transition-transform inline-block">»</span>
                                            <p class="font-medium italic">{{ point }}</p>
                                        </li>
                                    </ul>
                                </div>
                            </div>

                            <!-- Decorative Node Pulse (Active State) -->
                            <div
                                class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 hidden md:flex items-center justify-center z-10">
                                <div class="node-wrapper relative">
                                    <div
                                        class="w-4 h-4 rounded-full bg-primary/20 absolute -inset-2 blur-md opacity-0 active-glow">
                                    </div>
                                    <div
                                        class="w-3 h-3 rounded-full bg-white/20 border border-white/30 pulse-node transition-colors duration-500">
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Education Stream Nodes -->
                        <div v-for="(edu, index) in education" :key="'edu-' + index"
                            class="stream-item relative grid md:grid-cols-2 gap-10 md:gap-32">
                            <!-- Left: Detailed Content (Alternating logic via class) -->
                            <div class="stream-content order-2 md:order-1 self-center"
                                :class="index % 2 === 0 ? 'md:text-right' : 'md:order-2'">
                                <div class="space-y-8">
                                    <div class="flex items-center gap-4"
                                        :class="index % 2 === 0 ? 'md:flex-row-reverse md:justify-start' : ''">
                                        <div class="w-8 h-[1px] bg-white/20"></div>
                                        <span
                                            class="text-xs font-mono text-white/30 uppercase tracking-[0.4em]">ACADEMIC_ARC_0{{
                                                index + 1 }}</span>
                                    </div>
                                    <h5
                                        class="text-2xl sm:text-3xl md:text-6xl font-black italic uppercase leading-tight">
                                        {{ edu.title }}
                                    </h5>
                                    <div class="text-white/40 group relative inline-block">
                                        <p class="text-lg font-bold italic tracking-wide text-white/60">{{
                                            edu.institution
                                        }}</p>
                                        <p class="text-[10px] uppercase tracking-[0.5em] mt-2 opacity-50">{{
                                            edu.location }}
                                        </p>
                                    </div>
                                    <p class="text-white/30 text-sm leading-relaxed max-w-md italic"
                                        :class="index % 2 === 0 ? 'md:ml-auto' : ''">{{ edu.desc }}</p>
                                    <div class="flex items-center gap-6 pt-4"
                                        :class="index % 2 === 0 ? 'justify-end' : ''">
                                        <div class="h-[1px] flex-1 bg-white/5"></div>
                                        <div class="text-right">
                                            <span
                                                class="block text-[9px] font-black text-primary uppercase">Grade_Index</span>
                                            <span class="text-4xl font-black italic">{{ edu.grade }}</span>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <!-- Right: Year / Visual Node -->
                            <div class="flex items-center justify-center order-1 md:order-2"
                                :class="index % 2 === 0 ? '' : 'md:order-1'">
                                <div class="relative group/edu-node">
                                    <!-- Holographic Frame -->
                                    <div
                                        class="absolute inset-0 bg-primary/10 blur-[60px] rounded-full scale-0 group-hover/edu-node:scale-100 transition-transform duration-1000 opacity-20">
                                    </div>

                                    <div class="relative flex flex-col items-center justify-center">
                                        <div
                                            class="text-6xl sm:text-8xl md:text-[11rem] font-black italic text-white/[0.02] outline-text-v2 uppercase leading-none transform group-hover/edu-node:scale-110 transition-transform duration-1000">
                                            {{ edu.period.split(' - ')[1] }}
                                        </div>

                                        <div class="absolute flex flex-col items-center">
                                            <div
                                                class="w-24 h-24 md:w-32 md:h-32 rounded-3xl bg-[#0A0F1E] border border-white/10 flex items-center justify-center relative overflow-hidden group-hover/edu-node:border-primary/50 transition-all duration-700 shadow-2xl">
                                                <div
                                                    class="absolute inset-0 bg-gradient-to-br from-primary/10 via-transparent to-transparent">
                                                </div>
                                                <div class="absolute -inset-2 bg-primary/5 blur-xl animate-pulse"></div>

                                                <GraduationCapIcon size="44" stroke-width="1"
                                                    class="text-white/40 group-hover/edu-node:text-primary transition-all duration-700 z-10" />

                                                <!-- Scanning Line -->
                                                <div
                                                    class="absolute inset-0 w-full h-[2px] bg-primary/30 -translate-y-full animate-scan">
                                                </div>
                                            </div>

                                            <div
                                                class="mt-4 px-4 py-1 bg-primary/10 border border-primary/20 rounded-full scale-0 group-hover/edu-node:scale-100 transition-transform duration-500">
                                                <span
                                                    class="text-[9px] font-mono text-primary font-bold uppercase tracking-tighter">SUCCESSION_COMPLETE</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <!-- Alternate Decorative Node Position -->
                            <div
                                class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 hidden md:flex items-center justify-center z-10">
                                <div
                                    class="w-4 h-4 rounded-full border border-primary/30 flex items-center justify-center pulse-node">
                                    <div class="w-1.5 h-1.5 rounded-full bg-primary/40"></div>
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
    Code2Icon, SparklesIcon, TargetIcon, SearchIcon, LayersIcon, ShieldCheckIcon, TerminalIcon, BriefcaseIcon, GraduationCapIcon, ZapIcon, CpuIcon, RocketIcon, ActivityIcon, Building2Icon, MapPinIcon, LaptopIcon, PaletteIcon, LeafIcon, SwordsIcon, TargetIcon as GoalIcon,
    MailIcon, PhoneIcon, CalendarIcon, CheckCircleIcon, UserIcon, GlobeIcon
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

const impactStats = [
    { label: 'Syste_Logic_Efficiency', val: 99, suffix: '%' },
    { label: 'Application_Scaling', val: 50, suffix: '+' },
    { label: 'Uptime_Reliability', val: 100, suffix: '%' },
]

const archiveItems = [
    { title: 'Scalable Architecture', sub: 'High-Performance Backend ecosystems', icon: CpuIcon },
    { title: 'Nexus Interfaces', sub: 'Modern frontend fluid mechanics', icon: LaptopIcon },
    { title: 'Security Protocols', sub: 'Encrypted deployment matrices', icon: ShieldCheckIcon },
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
    { label: 'RESIDENCE', value: 'Dhaka, Bangladesh', icon: MapPinIcon },
    { label: 'TEMPORAL', value: '31 Oct 2003 (21y)', icon: CalendarIcon },
    { label: 'ACADEMIC', value: 'Diploma in CSE', icon: GraduationCapIcon },
    { label: 'EMAIL', value: 'ashikurrahman7194@gmail.com', icon: MailIcon },
    { label: 'CONTACT', value: '+8801700-917194', icon: PhoneIcon },
    { label: 'STATUS', value: 'Available for Excellence', icon: CheckCircleIcon },
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
        // Core Pillars: Modern Header Slide Reveal
        const pillarTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.pillar-header',
                start: 'top 85%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            }
        })

        pillarTl.to('.pillar-label', { opacity: 1, y: 0, duration: 1, ease: 'expo.out' })
            .to('.pillar-slide-text', { opacity: 1, x: 0, duration: 1.2, stagger: 0.1, ease: 'expo.out' }, '-=0.7')
            .to('.pillar-accent', { opacity: 1, y: 0, duration: 1, ease: 'power3.out' }, '-=0.5')

        // Core Pillars: Bidirectional Card Reveal
        // Core Pillars: Directional Card Reveal
        gsap.utils.toArray('.pillar-card').forEach((card, i) => {
            // Main card directional entrance
            const xOffset = i === 0 ? -150 : (i === 2 ? 150 : 0);
            const yOffset = i === 1 ? 80 : 50;
            const scaleOffset = i === 1 ? 0.9 : 1;

            gsap.from(card, {
                scrollTrigger: {
                    trigger: card,
                    start: 'top 92%',
                    end: 'bottom 10%',
                    toggleActions: 'play reverse play reverse',
                },
                x: xOffset,
                y: yOffset,
                scale: scaleOffset,
                opacity: 0,
                duration: 1.5,
                ease: 'expo.out'
            })

            // Inner elements (Icon, Title, Description) reveal
            const content = card.querySelector('.pillar-content');
            if (content) {
                gsap.from(content.children, {
                    scrollTrigger: {
                        trigger: card,
                        start: 'top 85%',
                        end: 'bottom 15%',
                        toggleActions: 'play reverse play reverse',
                    },
                    y: 20,
                    opacity: 0,
                    stagger: 0.15,
                    duration: 1.2,
                    ease: 'power3.out',
                    delay: 0.2
                })
            }
        })

        gsap.to('.pillar-bg-text', {
            scrollTrigger: {
                trigger: '.pillar-header',
                start: 'top bottom',
                end: 'bottom top',
                scrub: 1.5
            },
            y: -100,
            scale: 1.1
        })

        // DNA Section: Cinema Reveal
        const dnaTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.dna-section',
                start: 'top 80%',
                toggleActions: 'play none none reverse'
            }
        })

        dnaTl.to('.dna-line', { y: 0, duration: 1.5, ease: 'expo.out', stagger: 0.2 })
            .to('.reveal-dna', { opacity: 1, x: 0, y: 0, duration: 1.3, stagger: 0.1, ease: 'power4.out' }, '-=1')
            .to('.stat-value', {
                innerText: (i, el) => el.getAttribute('data-target'),
                duration: 2.5,
                snap: { innerText: 1 },
                ease: 'expo.out'
            }, '-=1')

        // Creative Protocol: Header Slide Reveal
        const protocolTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.protocol-header',
                start: 'top 85%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            }
        })

        protocolTl.to('.protocol-label', { opacity: 1, x: 0, duration: 1, ease: 'expo.out' })
            .to('.protocol-slide-text', { opacity: 1, x: 0, duration: 1.2, stagger: 0.1, ease: 'expo.out' }, '-=0.7')

        // Creative Protocol: Side-Curve
        gsap.from('.protocol-step', {
            scrollTrigger: { trigger: '.protocol-step', start: 'top 85%', end: 'top 30%', scrub: 1.2 },
            opacity: 0, scale: 0.4, x: (i) => (i % 2 === 0 ? -400 : 400), y: 200, rotation: (i) => (i % 2 === 0 ? -20 : 20), stagger: 0.1, ease: 'expo.out'
        })

        // Elite Stream: Advanced Kinetic Logic
        gsap.to('.conduit-progress', {
            scrollTrigger: { trigger: '.stream-section', start: 'top 30%', end: 'bottom 80%', scrub: true },
            scaleY: 1
        })

        // Elite Stream: Header Slide Reveal
        const headerTl = gsap.timeline({
            scrollTrigger: {
                trigger: '.stream-header',
                start: 'top 85%',
                end: 'bottom 20%',
                toggleActions: 'play reverse play reverse'
            }
        })

        headerTl.to('.stream-label', { opacity: 1, x: 0, duration: 1, ease: 'expo.out' })
            .to('.stream-slide-text', { opacity: 1, x: 0, duration: 1.2, stagger: 0.1, ease: 'expo.out' }, '-=0.7')
            .to('.header-tag', { opacity: 1, duration: 1 }, '-=0.5')

        // Parallax Background
        gsap.to('.succession-text', {
            scrollTrigger: { trigger: '.stream-section', start: 'top bottom', end: 'bottom top', scrub: 1 },
            y: -300,
            rotate: -2
        })

        const streamItems = gsap.utils.toArray('.stream-item')

        // Scroll Velocity Skew Effect
        let proxy = { skew: 0 },
            skewSetter = gsap.quickSetter('.stream-item', 'skewY', 'deg'),
            clamp = gsap.utils.clamp(-10, 10);

        ScrollTrigger.create({
            onUpdate: (self) => {
                let skew = clamp(self.getVelocity() / -300);
                if (Math.abs(skew) > Math.abs(proxy.skew)) {
                    proxy.skew = skew;
                    gsap.to(proxy, {
                        skew: 0,
                        duration: 0.8,
                        ease: 'power3',
                        overwrite: true,
                        onUpdate: () => skewSetter(proxy.skew)
                    });
                }
            }
        });

        streamItems.forEach((item, i) => {
            const content = item.querySelector('.stream-content')
            const meta = item.querySelector('.stream-meta')
            const node = item.querySelector('.pulse-node')
            const activeGlow = item.querySelector('.active-glow')

            const tl = gsap.timeline({
                scrollTrigger: {
                    trigger: item,
                    start: 'top 80%',
                    end: 'top 20%',
                    toggleActions: 'play none none reverse',
                }
            })

            tl.from(node, { scale: 0, opacity: 0, duration: 1, ease: 'elastic.out(1, 0.3)' })
                .to(node, { backgroundColor: '#00d27b', borderColor: '#00d27b', duration: 0.5 }, '-=0.5')
                .to(activeGlow, { opacity: 1, scale: 2, duration: 1 }, '-=0.5')
                .from(meta, {
                    x: i % 2 === 0 ? -150 : 150,
                    opacity: 0,
                    duration: 1.2,
                    ease: 'expo.out'
                }, '-=0.8')
                .from(content, {
                    x: i % 2 === 0 ? 150 : -150,
                    opacity: 0,
                    duration: 1.2,
                    ease: 'expo.out'
                }, '-=1')
                .from(item.querySelectorAll('li'), {
                    opacity: 0,
                    y: 20,
                    stagger: 0.1,
                    duration: 0.8,
                    ease: 'power3.out'
                }, '-=0.5')
                .from(item.querySelectorAll('.outline-text, .outline-text-subtle'), {
                    opacity: 0,
                    scale: 0.9,
                    duration: 2,
                    ease: 'power4.out'
                }, '-=1.2')
        })

        gsap.from('.bio-content', { scrollTrigger: { trigger: '.bio-content', start: 'top 85%', end: 'top 30%', scrub: 1 }, x: -50, opacity: 0, ease: 'power2.out' })
        gsap.from('.bio-visual', { scrollTrigger: { trigger: '.bio-content', start: 'top 85%', end: 'top 30%', scrub: 1.5 }, scale: 0.9, opacity: 0.2, y: 100, ease: 'power3.out' })

        // 1. Fast Snappy Reveal on Preloader Complete
        window.addEventListener('preloaderComplete', () => {
            gsap.to('.personal-card', {
                opacity: 1,
                x: 0,
                y: 0,
                duration: 0.8,
                stagger: 0.05,
                ease: 'expo.out',
                delay: 0.2
            })
        })

        // 2. Personalized Unique Entrances for Each Card on Scroll
        gsap.utils.toArray('.personal-card').forEach((card, i) => {
            let initialProps = { opacity: 0 }

            // Assign unique animation based on index
            if (i === 0) initialProps.x = -100 // Residence: Slide from Left
            else if (i === 1) initialProps.x = 100 // Temporal: Slide from Right
            else if (i === 2) initialProps.y = 100 // Academic: Rise from Bottom
            else if (i === 3) { initialProps.y = -50; initialProps.rotateX = 90 } // Email: Flip from Top
            else if (i === 4) { initialProps.skewX = 20; initialProps.x = 50 } // Contact: Skew slide
            else if (i === 5) initialProps.scale = 0.5 // Status: Pop up

            gsap.fromTo(card,
                initialProps,
                {
                    x: 0,
                    y: 0,
                    opacity: 1,
                    scale: 1,
                    rotateX: 0,
                    skewX: 0,
                    duration: 0.6,
                    ease: i === 2 ? "back.out(1.2)" : "expo.out",
                    scrollTrigger: {
                        trigger: card,
                        start: "top bottom-=50",
                        toggleActions: "play reverse play reverse"
                    }
                }
            )
        })
    }, aboutRef.value)
})
</script>

<style scoped>
.m-line {
    transform: translateY(100%);
}

.outline-text-v2 {
    -webkit-text-stroke: 1.5px rgba(255, 255, 255, 0.08);
    color: transparent;
    transition: all 0.7s cubic-bezier(0.23, 1, 0.32, 1);
}

.group:hover .outline-text-v2 {
    -webkit-text-stroke: 1.5px rgba(0, 210, 123, 0.3);
    color: rgba(255, 255, 255, 0.02);
}

@keyframes scan {
    0% {
        transform: translateY(-100%);
    }

    100% {
        transform: translateY(400%);
    }
}

.animate-scan {
    animation: scan 3s linear infinite;
}

.s-glitch {
    position: relative;
}

.s-glitch::after {
    content: attr(data-text);
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #020408;
    color: #00d27b;
    clip-path: polygon(0 0, 100% 0, 100% 45%, 0 45%);
    transform: translate(-0.025em, -0.0125em);
    opacity: 0.8;
    animation: glitch 2s infinite linear alternate-reverse;
}

@keyframes glitch {
    0% {
        clip-path: polygon(0 2%, 100% 2%, 100% 5%, 0 5%);
        transform: translate(2px, -2px);
    }

    10% {
        clip-path: polygon(0 15%, 100% 15%, 100% 15%, 0 15%);
    }

    20% {
        clip-path: polygon(0 10%, 100% 10%, 100% 20%, 0 20%);
        transform: translate(-2px, 2px);
    }

    100% {
        clip-path: polygon(0 100%, 100% 100%, 100% 100%, 0 100%);
    }
}

@keyframes pulse-node-glow {
    0% {
        transform: scale(1);
        opacity: 0.5;
    }

    50% {
        transform: scale(1.2);
        opacity: 1;
    }

    100% {
        transform: scale(1);
        opacity: 0.5;
    }
}

.pulse-node {
    animation: pulse-node-glow 4s infinite ease-in-out;
}

.stream-section {
    perspective: 2000px;
}

.stream-item {
    will-change: transform, opacity;
    transform-style: preserve-3d;
}

.stream-content {
    transition: transform 0.3s ease-out;
}

.stream-item:hover .pulse-node {
    background-color: #00d27b !important;
    box-shadow: 0 0 20px rgba(0, 210, 123, 0.6);
}

@keyframes float {
    from {
        transform: translateY(0) translateX(0);
    }

    to {
        transform: translateY(-100vh) translateX(20px);
    }
}
</style>
