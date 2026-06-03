<template>
  <section id="portfolio" class="portfolio-section">
    <div class="container">
      <div class="section-header">
        <p class="section-eyebrow">My Work</p>
        <h2 class="section-title">My <em>Portfolio</em></h2>
        <p class="section-sub">Latest projects showcasing modern web development and creative design solutions.</p>
      </div>

      <div class="projects-grid">
        <a
          v-for="project in projects"
          :key="project.title"
          :href="project.href || '#'"
          :target="project.href ? '_blank' : undefined"
          rel="noopener noreferrer"
          class="project-card"
          :class="{ featured: project.featured }"
        >
          <!-- REPLACE with this -->
<div class="project-thumb">
  <img :src="project.image" :alt="project.title" class="thumb-img" />
  <span v-if="project.featured" class="feat-badge">Featured</span>
</div>
          <div class="project-body">
  <h3 class="project-title">{{ project.title }}</h3>
  <p class="project-desc">{{ project.desc }}</p>

  <div class="tags">
    <span v-for="tag in project.tags" :key="tag" class="tag">
      {{ tag }}
    </span>
  </div>

  <div class="project-links">
    <a
      v-if="project.href"
      :href="project.href"
      target="_blank"
      class="btn-link"
      @click.stop
    >
      Live Demo
    </a>

    <a
      v-if="project.github"
      :href="project.github"
      target="_blank"
      class="btn-link github"
      @click.stop
    >
      GitHub
    </a>
  </div>
</div>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { defineComponent, h } from 'vue'

const IconLeaf = defineComponent({ render: () => h('svg', { width:40, height:40, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':1.2 }, [h('path', { d:'M11 20A7 7 0 0 1 9.8 6.1C15.5 5 17 4.48 19 2c1 2 2 4.18 2 8 0 5.5-4.78 10-10 10z' }), h('path', { d:'M2 21c0-3 1.85-5.36 5.08-6C9.5 14.52 12 13 13 12' })]) })
const IconUser = defineComponent({ render: () => h('svg', { width:40, height:40, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':1.2 }, [h('circle', { cx:12, cy:8, r:4 }), h('path', { d:'M4 20c0-4 3.58-7 8-7s8 3 8 7' })]) })

const projects = [
  {
    title: 'Greenlife Plant Store',
    desc: 'A modern e-commerce website for plant enthusiasts...',
    tags: ['HTML', 'CSS', 'JavaScript', 'Responsive Design'],
    image: '/project-greenlife.png',
    featured: true,
    href: 'https://greenlifeplantshop.netlify.app/',
    github: 'https://github.com/Sreypy/GreenLifeShop',
  },
  {
    title: 'Khmer Organic Food',
    desc: 'A modern e-commerce website for organic food enthusiasts...',
    tags: ['Vue 3', 'JavaScript', 'CSS'],
    image: '/project-khmer-organic.png',
    featured: true,
    href: '',
    github: 'https://github.com/tithyarita/Khmer-organic-food-project',
  },
  {
    title: 'Library Management System',
    desc: 'A sleek library management app with drag-and-drop features...',
    tags: ['HTML', 'Java'],
    image: '/project-library.png',
    featured: true,
    href: '',
    github: 'https://github.com/tithyarita/Project4-Library-Borrowing-and-Book-Tracking-System',
  },
  {
    title: 'Baby Store',
    desc: 'A modern website mobile built with Flutter.',
    tags: ['flutter', 'dart'],
    image: '/project-baby-store.png',
    featured: true,
    href: '',
    github: 'https://github.com/Flutter-Mobile-Project/Baby-Store-Project',
  },
  {
    title: 'Jomnus project',
    desc: 'A modern website built with react.js and next.js.',
    tags: ['react.js', 'JavaScript', 'next.js'],
    image: '/project-jomnus.png',
    featured: true,
    href: '',
    github: 'https://github.com/IP2-Project'
  }
]
</script>

<style scoped>
.portfolio-section { padding: 100px 0; }
.section-eyebrow {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--purple-500);
  margin-bottom: 10px;
}
.section-title {
  font-size: clamp(28px, 4vw, 42px);
  color: var(--text-primary);
  letter-spacing: -0.03em;
  margin-bottom: 8px;
}
.section-title em { color: var(--purple-500); font-style: italic; }
.section-sub {
  font-size: 15px;
  color: var(--text-secondary);
  font-weight: 300;
  margin-bottom: 52px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
}
.project-card {
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  background: var(--surface);
  overflow: hidden;
  text-decoration: none;
  color: inherit;
  display: flex;
  flex-direction: column;
  transition: transform 0.25s, box-shadow 0.25s, border-color 0.25s;
}
.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 16px 40px rgba(0,0,0,0.08);
  border-color: var(--purple-200);
}
.project-card.featured { border-color: var(--purple-200); }

.project-thumb {
  height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
.thumb-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.thumb-icon { opacity: 0.7; }
.feat-badge {
  position: absolute;
  top: 14px;
  left: 14px;
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.06em;
  padding: 3px 10px;
  border-radius: 20px;
  background: var(--purple-50);
  color: var(--purple-800);
  border: 1px solid var(--purple-200);
  text-transform: uppercase;
}
.coming-soon-badge {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255,255,255,0.6);
  font-size: 13px;
  font-weight: 500;
  color: var(--text-secondary);
  letter-spacing: 0.05em;
}

.project-body { padding: 20px; flex: 1; }
.project-title {
  font-size: 16px;
  font-weight: 500;
  color: var(--text-primary);
  margin-bottom: 8px;
  font-family: 'DM Sans', sans-serif;
}
.project-desc {
  font-size: 13px;
  color: var(--text-secondary);
  line-height: 1.65;
  margin-bottom: 14px;
  font-weight: 300;
}
.tags { display: flex; flex-wrap: wrap; gap: 6px; }
.tag {
  font-size: 11px;
  padding: 3px 9px;
  border-radius: 20px;
  background: var(--bg);
  color: var(--text-secondary);
  border: 1px solid var(--border);
}
.project-links {
  display: flex;
  gap: 10px;
  margin-top: 16px;
}

.btn-link {
  padding: 8px 14px;
  border-radius: 8px;
  text-decoration: none;
  font-size: 13px;
  font-weight: 500;
  border: 1px solid var(--purple-200);
  transition: 0.2s ease;
}

.btn-link:hover {
  transform: translateY(-2px);
}

.github {
  background: #9e8fd5;
  color: white;
}
</style>
