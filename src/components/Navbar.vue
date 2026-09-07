<script setup lang="ts">
import { ref } from "vue";

const isMenuOpen = ref(false);

const navLinks = [
    { label: "Home", href: "#" },
    { label: "Characters", href: "#" },
    { label: "Light Cones", href: "#" },
    { label: "Relics", href: "#" },
];
</script>

<template>
    <nav class="bg-slate-900 border-b border-slate-700 shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <!-- Logo -->
                <div class="flex items-center gap-3">
                    <img src="/hsr-logo.webp" alt="Honkai: Star Rail Logo" class="h-9 w-auto object-contain" />
                    <span class="text-white font-bold text-lg tracking-wide">Honkai: Star Rail</span>
                </div>

                <!-- Desktop Links -->
                <div class="hidden md:flex items-center gap-1">
                    <a v-for="link in navLinks" :key="link.label" :href="link.href" class="text-slate-300 hover:text-amber-400 hover:bg-slate-800 px-4 py-2 rounded-md text-sm font-medium transition-colors duration-200">
                        {{ link.label }}
                    </a>
                </div>

                <!-- Mobile Hamburger -->
                <button class="md:hidden text-slate-300 hover:text-white p-2 rounded-md hover:bg-slate-800 transition-colors" @click="isMenuOpen = !isMenuOpen" aria-label="Toggle menu">
                    <svg v-if="!isMenuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                    <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div v-if="isMenuOpen" class="md:hidden border-t border-slate-700 bg-slate-800">
            <div class="px-4 py-3 space-y-1">
                <a v-for="link in navLinks" :key="link.label" :href="link.href" class="block text-slate-300 hover:text-amber-400 hover:bg-slate-700 px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200" @click="isMenuOpen = false">
                    {{ link.label }}
                </a>
            </div>
        </div>
    </nav>
</template>
