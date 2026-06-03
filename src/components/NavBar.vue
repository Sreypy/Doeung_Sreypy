<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container nav-inner">
      <a href="#home" class="brand">Doeung Sreypy</a>
      <div class="nav-links" :class="{ open: menuOpen }">
        <a v-for="link in links" :key="link.href" :href="link.href" class="nav-link" @click="menuOpen = false">
          {{ link.label }}
        </a>
      </div>
      <div class="nav-actions">
        <!-- Dark/Light toggle -->
        <button class="theme-toggle" @click="toggleTheme" :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'">
          <!-- Sun icon (show in dark mode) -->
          <svg v-if="isDark" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="5"/>
            <line x1="12" y1="1" x2="12" y2="3"/>
            <line x1="12" y1="21" x2="12" y2="23"/>
            <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
            <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
            <line x1="1" y1="12" x2="3" y2="12"/>
            <line x1="21" y1="12" x2="23" y2="12"/>
            <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
            <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
          </svg>
          <!-- Moon icon (show in light mode) -->
          <svg v-else width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
          </svg>
        </button>
        <!-- Hamburger -->
        <button class="hamburger" @click="menuOpen = !menuOpen" :class="{ open: menuOpen }" aria-label="Toggle menu">
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useTheme } from '../composables/useTheme.js'

const { isDark, toggleTheme } = useTheme()
const isScrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { href: '#home',      label: 'Home' },
  { href: '#about',     label: 'About' },
  { href: '#skills',    label: 'Skills' },
  { href: '#portfolio', label: 'Portfolio' },
  { href: '#contact',   label: 'Contact' },
]

const handleScroll = () => { isScrolled.value = window.scrollY > 40 }
onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  transition: background 0.3s, box-shadow 0.3s, padding 0.3s;
  padding: 20px 0;
}
.navbar.scrolled {
  background: rgba(var(--bg-rgb, 250,250,248), 0.92);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  box-shadow: 0 1px 0 var(--border);
  padding: 14px 0;
}
.dark .navbar.scrolled { background: rgba(15,15,14,0.92); }

.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.brand {
  font-family: 'DM Serif Display', serif;
  font-size: 18px;
  color: var(--text-primary);
  text-decoration: none;
  letter-spacing: -0.02em;
}
.nav-links {
  display: flex;
  gap: 32px;
}
.nav-link {
  font-size: 14px;
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 400;
  transition: color 0.2s;
}
.nav-link:hover { color: var(--purple-500); }

.nav-actions {
  display: flex;
  align-items: center;
  gap: 8px;
}

/* Theme toggle button */
.theme-toggle {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1px solid var(--border-md);
  background: var(--surface);
  color: var(--text-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s;
}
.theme-toggle:hover {
  border-color: var(--purple-200);
  color: var(--purple-500);
  transform: rotate(20deg);
}

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}
.hamburger span {
  display: block;
  width: 22px;
  height: 1.5px;
  background: var(--text-primary);
  transition: transform 0.3s, opacity 0.3s;
}
.hamburger.open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

@media (max-width: 640px) {
  .hamburger { display: flex; }
  .nav-links {
    display: none;
    position: absolute;
    top: 100%;
    left: 0; right: 0;
    background: var(--surface);
    flex-direction: column;
    padding: 20px 32px;
    gap: 20px;
    border-bottom: 1px solid var(--border);
    box-shadow: 0 8px 24px rgba(0,0,0,0.06);
  }
  .nav-links.open { display: flex; }
}
</style>