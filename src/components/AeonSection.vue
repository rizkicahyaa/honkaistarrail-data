<script setup lang="ts">
const aeons = [
    {
        name: "Nanook",
        title: "The Destruction",
        path: "Destruction",
        pathIcon: "/images/paths/destruction.webp",
        image: "/images/aeon/nanook.webp",
        description: "The Aeon of Destruction, embodying the belief that all things must eventually meet their end through conflict.",
    },
    {
        name: "Lan",
        title: "The Hunt",
        path: "Hunt",
        pathIcon: "/images/paths/hunt.webp",
        image: "/images/aeon/lan.webp",
        description: "The Aeon of the Hunt, representing the relentless pursuit of a singular, unwavering goal.",
    },
    {
        name: "Nous",
        title: "The Erudition",
        path: "Erudition",
        pathIcon: "/images/paths/erudition.webp",
        image: "/images/aeon/nous.webp",
        description: "The Aeon of Erudition, embodying the accumulation and mastery of all knowledge in the universe.",
    },
    {
        name: "Xipe",
        title: "The Harmony",
        path: "Harmony",
        pathIcon: "/images/paths/harmony.webp",
        image: "/images/aeon/xipe.webp",
        description: "The Aeon of Harmony, believed to be plural — a collective consciousness that fosters unity among beings.",
    },
    {
        name: "IX",
        title: "The Nihility",
        path: "Nihility",
        pathIcon: "/images/paths/nihility.webp",
        image: "/images/aeon/ix.webp",
        description: "The Aeon of Nihility, the embodiment of the void — an existence so absolute it denies all meaning.",
    },
    {
        name: "Qlipoth",
        title: "The Preservation",
        path: "Preservation",
        pathIcon: "/images/paths/preservation.webp",
        image: "/images/aeon/qlipoth.webp",
        description: "The Aeon of Preservation, an ancient fortress-like entity dedicated to shielding civilization from extinction.",
    },
    {
        name: "Yaoshi",
        title: "The Abundance",
        path: "Abundance",
        pathIcon: "/images/paths/abundance.webp",
        image: "/images/aeon/yaoshi.webp",
        description: "The Aeon of Abundance, spreading endless life across the cosmos — a blessing many consider a curse.",
    },
    {
        name: "Fuli",
        title: "The Remembrance",
        path: "Remembrance",
        pathIcon: "/images/paths/remembrance.png",
        image: "/images/aeon/fuli.webp",
        description: "The Aeon of Remembrance, keeper of all memories — ensuring nothing is ever truly forgotten.",
    },
    {
        name: "Aha",
        title: "The Elation",
        path: "Elation",
        pathIcon: "/images/paths/elation.png",
        image: "/images/aeon/aha.webp",
        description: "The Aeon of Elation, a capricious and theatrical entity who finds joy in twisting fate into comedy.",
    },
];
</script>

<template>
    <section id="aeon" class="aeon-section">
        <div class="aeon-container">
            <!-- Header -->
            <div class="aeon-header">
                <h2 class="aeon-title">Aeons</h2>
                <p class="aeon-subtitle">The divine beings who shape the Paths of the universe</p>
            </div>

            <!-- Grid -->
            <div class="aeon-grid">
                <div v-for="aeon in aeons" :key="aeon.name" class="aeon-card">
                    <!-- Image -->
                    <div class="aeon-img-wrap">
                        <img :src="aeon.image" :alt="aeon.name" class="aeon-img" />
                        <div class="aeon-img-overlay"></div>
                    </div>

                    <!-- Content -->
                    <div class="aeon-content">
                        <div class="aeon-path-badge">
                            <img :src="aeon.pathIcon" :alt="aeon.path" class="aeon-path-icon" />
                            <span>{{ aeon.path }}</span>
                        </div>
                        <h3 class="aeon-name">{{ aeon.name }}</h3>
                        <p class="aeon-title-text">{{ aeon.title }}</p>
                        <p class="aeon-desc">{{ aeon.description }}</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
/* Section */
.aeon-section {
    padding: 4rem 0;
    background-color: #030712;
    border-top: 1px solid #1e293b;
}

.aeon-container {
    max-width: 80rem;
    margin: 0 auto;
    padding: 0 1.5rem;
}

/* Header */
.aeon-header {
    text-align: center;
    margin-bottom: 3rem;
}

.aeon-title {
    font-size: 1.875rem;
    font-weight: 700;
    color: white;
    letter-spacing: 0.05em;
    margin-bottom: 0.5rem;
}

.aeon-subtitle {
    color: #94a3b8;
    font-size: 1rem;
}

/* Grid */
.aeon-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 1.25rem;
}

@media (min-width: 640px) {
    .aeon-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .aeon-grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

/* Card */
.aeon-card {
    display: flex;
    flex-direction: column;
    background-color: #0f172a;
    border: 1px solid #1e293b;
    border-radius: 0.875rem;
    overflow: hidden;
    transition: border-color 0.2s ease;
}

.aeon-card:hover {
    border-color: #fbbf24;
}

/* Image */
.aeon-img-wrap {
    position: relative;
    width: 100%;
    aspect-ratio: 16 / 7;
    overflow: hidden;
    background-color: #1e293b;
}

.aeon-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: top center;
    display: block;
}
/* 
.aeon-card:hover .aeon-img {
    transform: scale(1.05);
} */

.aeon-img-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to bottom, transparent 40%, rgba(15, 23, 42, 0.85) 100%);
}

/* Content */
.aeon-content {
    padding: 1rem 1.25rem 1.25rem;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    flex: 1;
}

.aeon-path-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.35rem;
    background-color: #1e293b;
    border-radius: 9999px;
    padding: 0.2rem 0.65rem;
    width: fit-content;
}

.aeon-path-icon {
    width: 14px;
    height: 14px;
    object-fit: contain;
}

.aeon-path-badge span {
    font-size: 0.7rem;
    color: #64748b;
    font-weight: 500;
}

.aeon-name {
    font-size: 1.2rem;
    font-weight: 700;
    color: white;
    margin: 0;
}

.aeon-title-text {
    font-size: 0.8rem;
    color: #fbbf24;
    font-weight: 500;
    margin: 0;
}

.aeon-desc {
    font-size: 0.82rem;
    color: #64748b;
    line-height: 1.6;
    margin: 0.25rem 0 0;
}
</style>
