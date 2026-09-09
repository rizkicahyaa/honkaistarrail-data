<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import HeroCarousel from "./components/HeroCarousel.vue";
import CharacterSection from "./components/CharacterSection.vue";
import PathSection from "./components/PathSection.vue";
</script>

<template>
    <div class="min-h-screen bg-slate-950 text-white" style="padding-top: 4rem">
        <Navbar />
        <HeroCarousel />
        <CharacterSection />
        <PathSection />
    </div>
</template>
