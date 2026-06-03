<template>
  <section id="about" class="about-section">
    <div class="container">
      <div class="section-header">
        <p class="section-eyebrow">Who I Am</p>
        <h2 class="section-title">About <em>Me</em></h2>
      </div>
      <div class="about-grid">
        <div class="about-text">
          <p>As a current student pursuing an Engineer's Degree in Information and Communication Engineering at the <strong>Institute of Technology of Cambodia</strong>, I've developed a strong foundation in both technical skills and design principles.</p>
          <p>My passion lies in creating beautiful, functional websites that not only look great but provide exceptional user experiences. I specialize in building responsive websites using modern web technologies, ensuring every project works seamlessly across all devices.</p>
          <p>What sets me apart is my love for learning and embracing challenges. I'm constantly exploring new technologies and design trends to deliver innovative solutions that exceed expectations.</p>
        </div>
        <div class="highlights">
          <div v-for="card in highlights" :key="card.title" class="h-card">
            <div class="h-icon">
              <component :is="card.icon" />
            </div>
            <div>
              <h3 class="h-title">{{ card.title }}</h3>
              <p class="h-desc">{{ card.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { defineComponent, h } from 'vue'

const IconBook = defineComponent({ render: () => h('svg', { width:20, height:20, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':1.5 }, [h('path', { d:'M22 10v6M2 10l10-5 10 5-10 5z' }), h('path', { d:'M6 12v5c3 3 9 3 12 0v-5' })]) })
const IconBolt = defineComponent({ render: () => h('svg', { width:20, height:20, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':1.5 }, [h('polygon', { points:'13,2 3,14 12,14 11,22 21,10 12,10 13,2' })]) })
const IconTarget = defineComponent({ render: () => h('svg', { width:20, height:20, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':1.5 }, [h('circle', { cx:12, cy:12, r:10 }), h('circle', { cx:12, cy:12, r:6 }), h('circle', { cx:12, cy:12, r:2 })]) })

const highlights = [
  { title: 'Education', desc: "Engineer's Degree in Information and Communication Engineering at ITC (2022–present)", icon: IconBook },
  { title: 'Fast Learner', desc: 'Quick to adapt and master new technologies, always staying ahead of industry trends', icon: IconBolt },
  { title: 'Challenge Lover', desc: 'Thrives on challenging tasks and complex problem-solving opportunities', icon: IconTarget },
]
</script>

<style scoped>
.about-section {
  padding: 100px 0;
  background: var(--surface);
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
}
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
  margin-bottom: 56px;
  letter-spacing: -0.03em;
}
.section-title em { color: var(--purple-500); font-style: italic; }

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: start;
}
.about-text p {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 16px;
  font-weight: 300;
}
.about-text strong { color: var(--text-primary); font-weight: 500; }

.highlights { display: flex; flex-direction: column; gap: 16px; }
.h-card {
  display: flex;
  gap: 16px;
  padding: 20px;
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  background: var(--bg);
  transition: border-color 0.2s, transform 0.2s;
}
.h-card:hover { border-color: var(--purple-200); transform: translateX(4px); }
.h-icon {
  width: 40px;
  height: 40px;
  border-radius: var(--radius-md);
  background: var(--purple-50);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  color: var(--purple-500);
}
.h-title { font-size: 14px; font-weight: 500; color: var(--text-primary); margin-bottom: 4px; font-family: 'DM Sans', sans-serif; }
.h-desc { font-size: 13px; color: var(--text-secondary); line-height: 1.6; font-weight: 300; }

@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; gap: 40px; }
}
</style>
