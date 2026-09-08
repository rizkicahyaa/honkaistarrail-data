<script setup lang="ts">
const characters = [
    { name: "Acheron",   path: "Nihility",    element: "Lightning", image: "/images/characters/acheron.webp"   },
    { name: "Bronya",    path: "Harmony",     element: "Wind",      image: "/images/characters/Bronya.webp"    },
    { name: "Ruan Mei",  path: "Harmony",     element: "Ice",       image: "/images/characters/ruan-mei.webp"  },
    { name: "Firefly",   path: "Destruction", element: "Fire",      image: "/images/characters/firefly.webp"   },
    { name: "Castorice", path: "Remembrance", element: "Quantum",   image: "/images/characters/castorice.webp" },
    { name: "Yao Guang", path: "Elation",     element: "Physical",  image: "/images/characters/yao-guang.webp" },
    { name: "Cyrene",    path: "Remembrance", element: "Ice",       image: "/images/characters/cyrene.webp"    },
    { name: "Hysilens",  path: "Nihility",    element: "Physical",  image: "/images/characters/hysilens.webp"  },
];

const elementColors: Record<string, string> = {
    Lightning: "#a78bfa",
    Wind:      "#34d399",
    Fire:      "#fb923c",
    Ice:       "#67e8f9",
    Physical:  "#e2e8f0",
    Quantum:   "#818cf8",
    Imaginary: "#fbbf24",
};
</script>

<template>
    <section class="char-section">
        <div class="char-container">

            <!-- Header -->
            <div class="char-header">
                <h2 class="char-title">Characters</h2>
                <p class="char-subtitle">Explore the Trailblazers of Honkai: Star Rail</p>
            </div>

            <!-- Grid -->
            <div class="char-grid">
                <div
                    v-for="char in characters"
                    :key="char.name"
                    class="char-card"
                >
                    <!-- Image -->
                    <div class="char-img-wrap">
                        <img
                            :src="char.image"
                            :alt="char.name"
                            class="char-img"
                        />
                    </div>

                    <!-- Info -->
                    <div class="char-info">
                        <span class="char-name">{{ char.name }}</span>
                        <div class="char-meta">
                            <span
                                class="char-element"
                                :style="{ color: elementColors[char.element] }"
                            >● {{ char.element }}</span>
                            <span class="char-path">{{ char.path }}</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- View All -->
            <div class="char-footer">
                <a href="#" class="char-btn">View All Characters</a>
            </div>

        </div>
    </section>
</template>

<style scoped>
/* Section */
.char-section {
    padding: 4rem 0;
    background-color: #020617;
}

.char-container {
    max-width: 80rem;
    margin: 0 auto;
    padding: 0 1.5rem;
}

/* Header */
.char-header {
    text-align: center;
    margin-bottom: 2.5rem;
}

.char-title {
    font-size: 1.875rem;
    font-weight: 700;
    color: white;
    letter-spacing: 0.05em;
    margin-bottom: 0.5rem;
}

.char-subtitle {
    color: #94a3b8;
    font-size: 1rem;
}

/* Grid */
.char-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
}

@media (min-width: 640px) {
    .char-grid { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1024px) {
    .char-grid { grid-template-columns: repeat(4, 1fr); }
}

/* Card */
.char-card {
    background-color: #0f172a;
    border: 1px solid #1e293b;
    border-radius: 0.75rem;
    overflow: hidden;
    cursor: pointer;
}

/* Image */
.char-img-wrap {
    width: 100%;
    aspect-ratio: 3 / 4;
    background-color: #1e293b;
    overflow: hidden;
}

.char-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: top;
    transition: transform 0.5s ease;
}

.char-card:hover .char-img {
    transform: scale(1.1);
}

/* Info */
.char-info {
    padding: 0.75rem 1rem;
}

.char-name {
    display: block;
    color: white;
    font-weight: 600;
    font-size: 0.875rem;
    margin-bottom: 0.25rem;
}

.char-meta {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 0.5rem;
}

.char-element {
    font-size: 0.75rem;
    font-weight: 500;
}

.char-path {
    font-size: 0.65rem;
    color: #64748b;
    background-color: #1e293b;
    padding: 0.1rem 0.5rem;
    border-radius: 9999px;
}

/* Footer */
.char-footer {
    text-align: center;
    margin-top: 2.5rem;
}

.char-btn {
    display: inline-block;
    padding: 0.625rem 2rem;
    border: 1px solid #fbbf24;
    color: #fbbf24;
    border-radius: 0.5rem;
    font-size: 0.875rem;
    font-weight: 600;
    text-decoration: none;
    transition: background-color 0.2s, color 0.2s;
}

.char-btn:hover {
    background-color: #fbbf24;
    color: #020617;
}
</style>

