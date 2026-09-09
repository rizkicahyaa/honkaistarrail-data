<script setup lang="ts">
const paths = [
    {
        name: "Destruction",
        image: "/images/paths/destruction.webp",
        description: "Those who walk the path of Destruction choose to face their fate head-on.",
    },
    {
        name: "Hunt",
        image: "/images/paths/hunt.webp",
        description: "Followers of the Hunt pursue their quarry with unwavering precision.",
    },
    {
        name: "Erudition",
        image: "/images/paths/erudition.webp",
        description: "Seekers of knowledge who believe wisdom is the greatest power.",
    },
    {
        name: "Harmony",
        image: "/images/paths/harmony.webp",
        description: "Those who maintain balance empower allies through unity and support.",
    },
    {
        name: "Nihility",
        image: "/images/paths/nihility.webp",
        description: "Walkers of the Void embrace nothingness to weaken and corrupt foes.",
    },
    {
        name: "Preservation",
        image: "/images/paths/preservation.webp",
        description: "Guardians who shield allies from harm through unyielding defense.",
    },
    {
        name: "Abundance",
        image: "/images/paths/abundance.webp",
        description: "Healers who follow the path of life and restoration.",
    },
    {
        name: "Remembrance",
        image: "/images/paths/remembrance.png",
        description: "Those who carry the weight of memory and shape the world through recollection.",
    },
    {
        name: "Elation",
        image: "/images/paths/elation.png",
        description: "Joyful warriors who turn battle into a theatrical performance.",
    },
];
</script>

<template>
    <section class="path-section">
        <div class="path-container">

            <!-- Header -->
            <div class="path-header">
                <h2 class="path-title">Paths</h2>
                <p class="path-subtitle">Each Path grants a unique role and fighting style</p>
            </div>

            <!-- Grid -->
            <div class="path-grid">
                <div
                    v-for="path in paths"
                    :key="path.name"
                    class="path-card"
                >
                    <div class="path-icon-wrap">
                        <img
                            :src="path.image"
                            :alt="path.name"
                            class="path-icon"
                        />
                    </div>
                    <div class="path-info">
                        <span class="path-name">{{ path.name }}</span>
                        <p class="path-desc">{{ path.description }}</p>
                    </div>
                </div>
            </div>

        </div>
    </section>
</template>

<style scoped>
/* Section */
.path-section {
    padding: 4rem 0;
    background-color: #040d1a;
    border-top: 1px solid #1e293b;
}

.path-container {
    max-width: 80rem;
    margin: 0 auto;
    padding: 0 1.5rem;
}

/* Header */
.path-header {
    text-align: center;
    margin-bottom: 2.5rem;
}

.path-title {
    font-size: 1.875rem;
    font-weight: 700;
    color: white;
    letter-spacing: 0.05em;
    margin-bottom: 0.5rem;
}

.path-subtitle {
    color: #94a3b8;
    font-size: 1rem;
}

/* Grid */
.path-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
}

@media (min-width: 640px) {
    .path-grid { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1024px) {
    .path-grid { grid-template-columns: repeat(3, 1fr); }
}

/* Card */
.path-card {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    background-color: #0f172a;
    border: 1px solid #1e293b;
    border-radius: 0.75rem;
    padding: 1.25rem 1rem;
    transition: border-color 0.2s;
}

.path-card:hover {
    border-color: #fbbf24;
}

/* Icon */
.path-icon-wrap {
    flex-shrink: 0;
    width: 48px;
    height: 48px;
    background-color: #1e293b;
    border-radius: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.5rem;
}

.path-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
}

/* Info */
.path-info {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
}

.path-name {
    color: white;
    font-size: 1rem;
    font-weight: 600;
}

.path-desc {
    color: #64748b;
    font-size: 0.8rem;
    line-height: 1.5;
    margin: 0;
}
</style>
