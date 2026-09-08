<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import HeroCarousel from "./components/HeroCarousel.vue";
import CharacterSection from "./components/CharacterSection.vue";
</script>

<template>
    <div class="min-h-screen bg-slate-950 text-white">
        <Navbar />
        <HeroCarousel />
        <CharacterSection />
    </div>
</template>
