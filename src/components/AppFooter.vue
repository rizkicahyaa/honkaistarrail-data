<script setup lang="ts">
const navLinks = [
    { label: "Home",         href: "#" },
    { label: "Characters",   href: "#" },
    { label: "Light Cones",  href: "#" },
    { label: "Relics",       href: "#" },
];

const paths = [
    "Destruction", "Hunt", "Erudition",
    "Harmony", "Nihility", "Preservation",
    "Abundance", "Remembrance", "Elation",
];

const currentYear = new Date().getFullYear();
</script>

<template>
    <footer class="footer">
        <div class="footer-container">

            <!-- Top -->
            <div class="footer-top">

                <!-- Brand -->
                <div class="footer-brand">
                    <div class="footer-logo-wrap">
                        <img src="/hsr-logo.webp" alt="Honkai: Star Rail" class="footer-logo" />
                        <span class="footer-brand-name">Honkai: Star Rail</span>
                    </div>
                    <p class="footer-brand-desc">
                        A fan-made database for Honkai: Star Rail — characters, light cones, relics, and more.
                    </p>
                </div>

                <!-- Nav Links -->
                <div class="footer-col">
                    <h3 class="footer-col-title">Navigation</h3>
                    <ul class="footer-links">
                        <li v-for="link in navLinks" :key="link.label">
                            <a :href="link.href" class="footer-link">{{ link.label }}</a>
                        </li>
                    </ul>
                </div>

                <!-- Paths -->
                <div class="footer-col">
                    <h3 class="footer-col-title">Paths</h3>
                    <ul class="footer-links footer-links--two-col">
                        <li v-for="path in paths" :key="path">
                            <a href="#" class="footer-link">{{ path }}</a>
                        </li>
                    </ul>
                </div>

            </div>

            <!-- Divider -->
            <div class="footer-divider"></div>

            <!-- Bottom -->
            <div class="footer-bottom">
                <p class="footer-copy">
                    &copy; {{ currentYear }} Honkai: Star Rail Database. Fan-made, not affiliated with HoYoverse.
                </p>
                <p class="footer-hoyoverse">
                    Honkai: Star Rail is a trademark of HoYoverse.
                </p>
            </div>

        </div>
    </footer>
</template>

<style scoped>
/* Footer */
.footer {
    background-color: #020617;
    border-top: 1px solid #1e293b;
    padding: 3rem 0 1.5rem;
}

.footer-container {
    max-width: 80rem;
    margin: 0 auto;
    padding: 0 1.5rem;
}

/* Top Grid */
.footer-top {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
}

@media (min-width: 640px) {
    .footer-top { grid-template-columns: 1fr 1fr; }
}

@media (min-width: 1024px) {
    .footer-top { grid-template-columns: 2fr 1fr 1fr; }
}

/* Brand */
.footer-logo-wrap {
    display: flex;
    align-items: center;
    gap: 0.625rem;
    margin-bottom: 0.75rem;
}

.footer-logo {
    width: 2rem;
    height: 2rem;
    object-fit: contain;
}

.footer-brand-name {
    color: white;
    font-weight: 700;
    font-size: 1rem;
    letter-spacing: 0.03em;
}

.footer-brand-desc {
    color: #475569;
    font-size: 0.85rem;
    line-height: 1.6;
    margin: 0;
    max-width: 24rem;
}

/* Columns */
.footer-col-title {
    color: #94a3b8;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 0.875rem;
}

.footer-links {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.footer-links--two-col {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 0.4rem 1rem;
}

.footer-link {
    color: #475569;
    font-size: 0.875rem;
    text-decoration: none;
    transition: color 0.2s;
}

.footer-link:hover {
    color: #fbbf24;
}

/* Divider */
.footer-divider {
    border-top: 1px solid #1e293b;
    margin: 2rem 0 1.25rem;
}

/* Bottom */
.footer-bottom {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    align-items: center;
    text-align: center;
}

@media (min-width: 640px) {
    .footer-bottom {
        flex-direction: row;
        justify-content: space-between;
        text-align: left;
    }
}

.footer-copy {
    color: #334155;
    font-size: 0.8rem;
    margin: 0;
}

.footer-hoyoverse {
    color: #1e293b;
    font-size: 0.75rem;
    margin: 0;
}
</style>
