<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container nav-inner">
      <a href="#home" class="brand">Doeung Sreypy</a>
      <div class="nav-links" :class="{ open: menuOpen }">
        <a v-for="link in links" :key="link.href" :href="link.href" class="nav-link" @click="menuOpen = false">
          {{ link.label }}
        </a>
      </div>
      <button class="hamburger" @click="menuOpen = !menuOpen" :class="{ open: menuOpen }" aria-label="Toggle menu">
        <span></span><span></span><span></span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { href: '#home', label: 'Home' },
  { href: '#about', label: 'About' },
  { href: '#skills', label: 'Skills' },
  { href: '#portfolio', label: 'Portfolio' },
  { href: '#contact', label: 'Contact' },
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
  transition: background 0.3s, box-shadow 0.3s;
  padding: 20px 0;
}
.navbar.scrolled {
  background: rgba(6, 6, 6, 0.92);
  backdrop-filter: blur(12px);
  box-shadow: 0 1px 0 var(--border);
  padding: 14px 0;
}
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
  letter-spacing: 0.01em;
}
.nav-link:hover { color: var(--purple-500); }
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
    box-shadow: 0 8px 24px rgba(8, 8, 8, 0.06);
  }
  .nav-links.open { display: flex; }
}
</style>
