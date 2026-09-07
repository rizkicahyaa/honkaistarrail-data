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
    <section>
        <div
            class="carousel-wrapper"
            @mouseenter="stopAuto"
            @mouseleave="startAuto"
        >
            <!-- Image -->
            <img
                :src="slides[current].src"
                :alt="slides[current].alt"
                class="carousel-image"
            />

            <!-- Overlay gradient -->
            <div class="carousel-overlay"></div>

            <!-- Prev Button -->
            <button class="carousel-btn carousel-btn--prev" @click="prev">
                <svg width="16" height="16" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
            </button>

            <!-- Next Button -->
            <button class="carousel-btn carousel-btn--next" @click="next">
                <svg width="16" height="16" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
            </button>

            <!-- Dot Indicators -->
            <div class="carousel-dots">
                <button
                    v-for="(_, i) in slides"
                    :key="i"
                    class="carousel-dot"
                    :class="{ 'carousel-dot--active': i === current }"
                    @click="goTo(i)"
                />
            </div>

            <!-- Slide Counter -->
            <div class="carousel-counter">
                {{ current + 1 }} / {{ slides.length }}
            </div>
        </div>
    </section>
</template>

<style scoped>
.carousel-wrapper {
    position: relative;
    width: 100%;
    max-height: 560px;
    overflow: hidden;
}

.carousel-image {
    width: 100%;
    max-height: 560px;
    object-fit: cover;
    transition: all 0.5s;
}

.carousel-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to bottom, transparent 50%, rgba(2, 6, 23, 0.7) 100%);
}

/* Nav Buttons */
.carousel-btn {
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
    transition: border-color 0.2s;
}

.carousel-btn:hover {
    border-color: #fbbf24;
}

.carousel-btn--prev {
    left: 1rem;
}

.carousel-btn--next {
    right: 1rem;
}

/* Dot Indicators */
.carousel-dots {
    position: absolute;
    bottom: 1rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 0.5rem;
    z-index: 10;
}

.carousel-dot {
    height: 8px;
    width: 8px;
    border-radius: 9999px;
    border: none;
    background: rgba(255, 255, 255, 0.4);
    cursor: pointer;
    padding: 0;
    transition: all 0.3s;
}

.carousel-dot--active {
    width: 24px;
    background: #fbbf24;
}

/* Slide Counter */
.carousel-counter {
    position: absolute;
    top: 1rem;
    right: 1rem;
    z-index: 10;
    font-size: 0.875rem;
    color: white;
    background: rgba(15, 23, 42, 0.6);
    border: 1px solid #334155;
    padding: 0.25rem 0.75rem;
    border-radius: 9999px;
}
</style>
