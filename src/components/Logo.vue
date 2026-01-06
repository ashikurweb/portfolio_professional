<template>
    <div class="flex items-center gap-4 group cursor-pointer select-none">
        <div class="relative w-12 h-12">
            <!-- Outer Rotating Rings -->
            <div
                class="absolute inset-0 border-2 border-primary/20 rounded-xl rotate-45 group-hover:rotate-[225deg] transition-transform duration-1000 ease-out">
            </div>
            <div
                class="absolute inset-2 border border-secondary/30 rounded-lg -rotate-12 group-hover:rotate-180 transition-transform duration-1000 ease-out">
            </div>

            <!-- Core Logo Shape -->
            <div class="absolute inset-0 flex items-center justify-center">
                <svg viewBox="0 0 100 100" class="w-8 h-8 filter drop-shadow-[0_0_8px_rgba(0,210,123,0.5)]">
                    <defs>
                        <linearGradient id="logo-grad-modern" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color: var(--color-primary); stop-opacity: 1" />
                            <stop offset="100%" style="stop-color: #00A3FF; stop-opacity: 1" />
                        </linearGradient>
                        <clipPath id="hexagon">
                            <path d="M50 5 L90 25 L90 75 L50 95 L10 75 L10 25 Z" />
                        </clipPath>
                    </defs>

                    <!-- Abstract "A" within Hexagon -->
                    <path d="M30 70 L50 20 L70 70 M40 55 L60 55" stroke="url(#logo-grad-modern)" stroke-width="12"
                        stroke-linecap="round" stroke-linejoin="round" fill="none" />

                    <!-- Floating Highlight -->
                    <circle cx="50" cy="20" r="5" fill="var(--color-secondary)" class="animate-pulse" />
                </svg>
            </div>

            <!-- Animated Glow Spot -->
            <div
                class="absolute -inset-1 bg-primary/20 blur-xl rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500">
            </div>
        </div>

        <div class="flex flex-col">
            <h1 class="text-2xl font-black tracking-tighter leading-none flex items-center">
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-white to-gray-400">ASHIKUR</span>
                <span class="text-primary ml-0.5 animate-bounce">.</span>
            </h1>
            <div class="flex items-center gap-2">
                <span class="h-[1px] w-4 bg-primary/50"></span>
                <span
                    class="text-[9px] uppercase tracking-[0.5em] font-bold text-gray-500 group-hover:text-primary/70 transition-colors">Innovator</span>
            </div>
        </div>
    </div>
</template>

<style scoped>
.group:hover .animate-bounce {
    animation: bounce 0.5s infinite;
}

@keyframes bounce {

    0%,
    100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(-3px);
    }
}
</style>
