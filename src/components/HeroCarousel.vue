<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const slides = [
    { src: "/images/1.png", alt: "Slide 1" },
    { src: "/images/2.png", alt: "Slide 2" },
    { src: "/images/3.png", alt: "Slide 3" },
    { src: "/images/4.png", alt: "Slide 4" },
];

const current = ref(0);
let timer: number | null = null;

function next() {
    current.value = (current.value + 1) % slides.length;
}

function prev() {
    current.value = (current.value - 1 + slides.length) % slides.length;
}

function goTo(i: number) {
    current.value = i;
}

function startAuto() {
    timer = window.setInterval(next, 4000);
}

function stopAuto() {
    if (timer !== null) {
        window.clearInterval(timer);
        timer = null;
    }
}

onMounted(startAuto);
onUnmounted(stopAuto);
</script>

<template>
    <section class="gallery" @mouseenter="stopAuto" @mouseleave="startAuto">
        <!-- Main Image -->
        <div class="gallery-main">
            <img :src="slides[current].src" :alt="slides[current].alt" class="gallery-img" />

            <!-- Overlay -->
            <div class="gallery-overlay"></div>

            <!-- Prev Button -->
            <button class="gallery-btn gallery-btn--prev" @click="prev">
                <svg width="16" height="16" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
            </button>

            <!-- Next Button -->
            <button class="gallery-btn gallery-btn--next" @click="next">
                <svg width="16" height="16" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
            </button>

            <!-- Counter -->
            <div class="gallery-counter">{{ current + 1 }} / {{ slides.length }}</div>
        </div>

        <!-- Thumbnail Panel (kanan) -->
        <div class="gallery-thumbs">
            <button v-for="(slide, i) in slides" :key="i" class="gallery-thumb" :class="{ 'gallery-thumb--active': i === current }" @click="goTo(i)">
                <img :src="slide.src" :alt="slide.alt" class="gallery-thumb-img" />
                <div class="gallery-thumb-overlay"></div>
            </button>
        </div>
    </section>
</template>

<style scoped>
.gallery {
    display: flex;
    width: 80%;
    background-color: #020617;
    gap: 3px;
    margin: 0 auto;
    margin-top: 30px;
}

/* Main image */
.gallery-main {
    position: relative;
    flex: 1;
    overflow: hidden;
}

.gallery-img {
    width: 100%;
    height: 100%;
    max-height: 620px;
    object-fit: cover;
    object-position: center top;
    display: block;
}

.gallery-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to right, transparent 60%, rgba(2, 6, 23, 0.3) 100%);
    pointer-events: none;
}

/* Nav Buttons */
.gallery-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 10;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: 1px solid #475569;
    background: rgba(15, 23, 42, 0.7);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition:
        border-color 0.2s,
        background 0.2s;
}

.gallery-btn:hover {
    border-color: #fbbf24;
    background: rgba(15, 23, 42, 0.95);
}

.gallery-btn--prev {
    left: 1rem;
}
.gallery-btn--next {
    right: 1rem;
}

/* Counter */
.gallery-counter {
    position: absolute;
    top: 1rem;
    left: 1rem;
    z-index: 10;
    font-size: 0.8rem;
    color: white;
    background: rgba(15, 23, 42, 0.65);
    border: 1px solid #334155;
    padding: 0.2rem 0.75rem;
    border-radius: 9999px;
}

/* Thumbnail panel kanan */
.gallery-thumbs {
    display: flex;
    flex-direction: column;
    gap: 3px;
    width: 160px;
    flex-shrink: 0;
}

@media (max-width: 640px) {
    .gallery {
        flex-direction: column;
    }
    .gallery-thumbs {
        flex-direction: row;
        width: 100%;
        height: 80px;
    }
    .gallery-btn--next {
        left: auto;
        right: 1rem;
    }
}

/* Thumbnail item */
.gallery-thumb {
    position: relative;
    flex: 1;
    overflow: hidden;
    border: 2px solid transparent;
    cursor: pointer;
    padding: 0;
    background: none;
    transition: border-color 0.2s;
}

.gallery-thumb--active {
    border-color: #fbbf24;
}

.gallery-thumb-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
    display: block;
    transition: transform 0.3s;
}

.gallery-thumb:hover .gallery-thumb-img {
    transform: scale(1.06);
}

.gallery-thumb-overlay {
    position: absolute;
    inset: 0;
    background: rgba(2, 6, 23, 0.35);
    transition: opacity 0.2s;
}

.gallery-thumb--active .gallery-thumb-overlay,
.gallery-thumb:hover .gallery-thumb-overlay {
    opacity: 0;
}
</style>
