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
    <nav class="navbar">
        <div class="navbar-container">
            <div class="navbar-inner">
                <!-- Logo -->
                <div class="navbar-brand">
                    <img src="/hsr-logo.webp" alt="Honkai: Star Rail Logo" class="navbar-logo" />
                    <span class="navbar-title">Honkai: Star Rail</span>
                </div>

                <!-- Desktop Links -->
                <div class="navbar-links">
                    <a
                        v-for="link in navLinks"
                        :key="link.label"
                        :href="link.href"
                        class="nav-link"
                    >
                        {{ link.label }}
                    </a>
                </div>

                <!-- Mobile Hamburger -->
                <button
                    class="navbar-hamburger"
                    @click="isMenuOpen = !isMenuOpen"
                    aria-label="Toggle menu"
                >
                    <svg v-if="!isMenuOpen" class="hamburger-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                    <svg v-else class="hamburger-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div v-if="isMenuOpen" class="mobile-menu">
            <div class="mobile-menu-inner">
                <a
                    v-for="link in navLinks"
                    :key="link.label"
                    :href="link.href"
                    class="mobile-nav-link"
                    @click="isMenuOpen = false"
                >
                    {{ link.label }}
                </a>
            </div>
        </div>
    </nav>
</template>

<style scoped>
/* Navbar */
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 50;
    background-color: #0f172a;
    border-bottom: 1px solid #334155;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.4);
}

.navbar-container {
    max-width: 80rem;
    margin: 0 auto;
    padding: 0 1rem;
}

@media (min-width: 640px) {
    .navbar-container { padding: 0 1.5rem; }
}

@media (min-width: 1024px) {
    .navbar-container { padding: 0 2rem; }
}

.navbar-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 4rem;
}

/* Brand */
.navbar-brand {
    display: flex;
    align-items: center;
    gap: 0.75rem;
}

.navbar-logo {
    height: 2.25rem;
    width: auto;
    object-fit: contain;
}

.navbar-title {
    color: white;
    font-weight: 700;
    font-size: 1.125rem;
    letter-spacing: 0.05em;
}

/* Desktop Links */
.navbar-links {
    display: none;
    align-items: center;
    gap: 0.25rem;
}

@media (min-width: 768px) {
    .navbar-links { display: flex; }
}

.nav-link {
    color: #cbd5e1;
    padding: 0.5rem 1rem;
    border-radius: 0.375rem;
    font-size: 0.875rem;
    font-weight: 500;
    text-decoration: none;
    transition: color 0.2s, background-color 0.2s;
}

.nav-link:hover {
    color: #fbbf24;
    background-color: #1e293b;
}

/* Hamburger */
.navbar-hamburger {
    display: flex;
    color: #cbd5e1;
    padding: 0.5rem;
    border-radius: 0.375rem;
    border: none;
    background: transparent;
    cursor: pointer;
    transition: color 0.2s, background-color 0.2s;
}

.navbar-hamburger:hover {
    color: white;
    background-color: #1e293b;
}

.hamburger-icon {
    width: 1.5rem;
    height: 1.5rem;
}

@media (min-width: 768px) {
    .navbar-hamburger { display: none; }
}

/* Mobile Menu */
.mobile-menu {
    border-top: 1px solid #334155;
    background-color: #1e293b;
}

@media (min-width: 768px) {
    .mobile-menu { display: none; }
}

.mobile-menu-inner {
    padding: 0.75rem 1rem;
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
}

.mobile-nav-link {
    display: block;
    color: #cbd5e1;
    padding: 0.5rem 0.75rem;
    border-radius: 0.375rem;
    font-size: 0.875rem;
    font-weight: 500;
    text-decoration: none;
    transition: color 0.2s, background-color 0.2s;
}

.mobile-nav-link:hover {
    color: #fbbf24;
    background-color: #334155;
}
</style>
