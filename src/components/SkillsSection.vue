<template>
  <section id="skills" class="skills-section">
    <div class="container">
      <div class="section-header">
        <p class="section-eyebrow">What I Work With</p>
        <h2 class="section-title">My <em>Skills</em></h2>
        <p class="section-sub">Technologies and tools I use to bring ideas to life.</p>
      </div>

      <div class="skills-grid">
        <div v-for="category in skillCategories" :key="category.title" class="skill-category">
          <div class="category-header">
            <div class="category-icon" :style="{ background: category.iconBg, color: category.iconColor }">
              <component :is="category.icon" />
            </div>
            <h3 class="category-title">{{ category.title }}</h3>
          </div>
          <div class="skill-list">
            <div v-for="skill in category.skills" :key="skill.name" class="skill-item">
              <span class="skill-logo" v-html="skill.logo"></span>
              <span class="skill-name">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="tools-row">
        <p class="tools-label">Tools & Others</p>
        <div class="tools-tags">
          <span
            v-for="tool in tools"
            :key="tool.name"
            class="tool-tag"
            :style="{ background: tool.bg, color: tool.color, borderColor: tool.border }"
          >
            <span class="tool-logo" v-html="tool.logo"></span>
            {{ tool.name }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { defineComponent, h } from 'vue'

const IconCode    = defineComponent({ render: () => h('svg', { width:18, height:18, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':2 }, [h('polyline',{points:'16 18 22 12 16 6'}), h('polyline',{points:'8 6 2 12 8 18'})]) })
const IconPalette = defineComponent({ render: () => h('svg', { width:18, height:18, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':2 }, [h('path',{d:'M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10c.926 0 1.648-.746 1.648-1.688 0-.437-.18-.835-.437-1.125-.29-.289-.438-.652-.438-1.125a1.64 1.64 0 0 1 1.668-1.668h1.996c3.051 0 5.555-2.503 5.555-5.554C21.965 6.012 17.461 2 12 2z'})]) })
const IconServer  = defineComponent({ render: () => h('svg', { width:18, height:18, viewBox:'0 0 24 24', fill:'none', stroke:'currentColor', 'stroke-width':2 }, [h('rect',{x:2,y:2,width:20,height:8,rx:2}), h('rect',{x:2,y:14,width:20,height:8,rx:2}), h('line',{x1:6,y1:6,x2:6.01,y2:6}), h('line',{x1:6,y1:18,x2:6.01,y2:18})]) })

const logos = {
  html: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#E44D26" d="M5 3l1.8 20.1L16 26l9.2-2.9L27 3z"/><path fill="#F16529" d="M16 24.4V5.5H25l-1.6 17.8z"/><path fill="#EBEBEB" d="M16 13.5H11.5l-.3-3.5H16V6.5H8.1l.8 9H16zm0 7.4l-.1.1-3.8-1-.2-2.8H8.6l.5 5.5 6.9 1.9z"/><path fill="#fff" d="M16 13.5v3.5h4.1l-.4 4.4-3.7 1v3.6l6.9-1.9 1-10.6z"/></svg>`,
  css: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#1572B6" d="M5 3l1.8 20.1L16 26l9.2-2.9L27 3z"/><path fill="#33A9DC" d="M16 24.4V5.5H25l-1.6 17.8z"/><path fill="#fff" d="M16 13.5H11.3l-.3-3.5H16V6.5H8.1l.8 9H16zm0 7.4v-3.5l-.1.1-3.8-1-.2-2.8H8.6l.5 5.5 6.9 1.9z"/><path fill="#EBEBEB" d="M16 13.5v3.5h3.8l-.4 4.4-3.4.9v3.6l6.9-1.9 1-10.6z"/></svg>`,
  js: `<svg viewBox="0 0 32 32" width="20" height="20"><rect width="32" height="32" rx="4" fill="#F7DF1E"/><path d="M9.7 25.1l2.1-1.3c.4.7.8 1.3 1.7 1.3.9 0 1.4-.3 1.4-1.7v-9h2.6v9.1c0 2.8-1.6 4-4 4-2.1 0-3.3-1.1-3.8-2.4zm10.1-.3l2.1-1.2c.5.9 1.2 1.5 2.4 1.5 1 0 1.6-.5 1.6-1.2 0-.8-.7-1.1-1.8-1.6l-.6-.3c-1.8-.8-3-1.7-3-3.8 0-1.9 1.4-3.3 3.7-3.3 1.6 0 2.7.6 3.5 2l-2 1.3c-.4-.8-.9-1.1-1.5-1.1s-1 .4-1 .9c0 .6.4.9 1.3 1.3l.6.3c2.1.9 3.3 1.8 3.3 3.9 0 2.2-1.7 3.5-4 3.5-2.3 0-3.7-1.1-4.6-2.7z"/></svg>`,
  vue: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#42b883" d="M16 3.6L8.5 17 5 11 13.9 3.6z"/><path fill="#35495e" d="M16 3.6L19.1 3.6 27 11 23.5 17z"/><path fill="#42b883" d="M16 28L2 6h5.5L16 21.2 24.5 6H30z"/><path fill="#35495e" d="M16 28L9.8 17.3 16 21.2 22.2 17.3z"/></svg>`,
  react: `<svg viewBox="0 0 32 32" width="20" height="20"><circle cx="16" cy="16" r="3" fill="#61DAFB"/><ellipse cx="16" cy="16" rx="12" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5"/><ellipse cx="16" cy="16" rx="12" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5" transform="rotate(60 16 16)"/><ellipse cx="16" cy="16" rx="12" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5" transform="rotate(120 16 16)"/></svg>`,
  next: `<svg viewBox="0 0 32 32" width="20" height="20"><circle cx="16" cy="16" r="14" fill="#000"/><path fill="#fff" d="M10.5 10h2v8.5l7-8.5h2.5L13.5 20.5 22 30h-2.5L10.5 18.5V10z"/></svg>`,
  node: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#339933" d="M16 3L4 9.5v13L16 29l12-6.5v-13L16 3zm0 2.3l9.7 5.3v10.8L16 26.7l-9.7-5.3V10.6L16 5.3z"/><path fill="#339933" d="M16 10a6 6 0 100 12A6 6 0 0016 10z"/></svg>`,
  nestjs: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#E0234E" d="M20.3 5.3c-.4-.2-.9-.1-1.2.2l-3.1 3-3.1-3c-.3-.3-.8-.4-1.2-.2C7.5 7 5 11.2 5 16c0 6.1 4.9 11 11 11s11-4.9 11-11c0-4.8-2.5-9-6.7-10.7z"/><path fill="#fff" d="M16 10a6 6 0 100 12A6 6 0 0016 10zm0 9.5a3.5 3.5 0 110-7 3.5 3.5 0 010 7z"/></svg>`,
  springboot: `<svg viewBox="0 0 32 32" width="20" height="20"><circle cx="16" cy="16" r="14" fill="#6DB33F"/><path fill="#fff" d="M9 16.5c0-3.9 3.1-7 7-7s7 3.1 7 7-3.1 7-7 7-7-3.1-7-7zm7-5c-2.8 0-5 2.2-5 5s2.2 5 5 5 5-2.2 5-5-2.2-5-5-5z"/><circle cx="22.5" cy="9.5" r="2" fill="#fff"/></svg>`,
  git: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#F05032" d="M29.5 14.5l-12-12a2.1 2.1 0 00-3 0l-2.6 2.6 3.3 3.3a2.5 2.5 0 013.2 3.2l3.2 3.2a2.5 2.5 0 11-1.5 1.5L17 13.9v8.4a2.5 2.5 0 11-2 0V13.7a2.5 2.5 0 01-1.4-3.3L10.4 7.1l-7.9 7.9a2.1 2.1 0 000 3l12 12a2.1 2.1 0 003 0l12-12a2.1 2.1 0 000-3z"/></svg>`,
  figma: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#F24E1E" d="M10 28a5 5 0 005-5v-5h-5a5 5 0 000 10z"/><path fill="#FF7262" d="M5 16a5 5 0 015-5h5v10h-5a5 5 0 01-5-5z"/><path fill="#A259FF" d="M5 6a5 5 0 015-5h5v10h-5A5 5 0 015 6z"/><path fill="#1ABCFE" d="M15 1h5a5 5 0 010 10h-5V1z"/><path fill="#0ACF83" d="M25 16a5 5 0 11-10 0 5 5 0 0110 0z"/></svg>`,
  flutter: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#54C5F8" d="M14.5 2L3 13.5l4 4L22.5 2z"/><path fill="#01579B" d="M14.5 18.5L10 23l4.5 4.5 4-4z"/><path fill="#29B6F6" d="M14.5 18.5l8-8-4-4-8 8z"/><path fill="#54C5F8" d="M18.5 22.5l-4 5h8z"/></svg>`,
  responsivedesign: `<svg viewBox="0 0 32 32" width="20" height="20"><rect x="2" y="6" width="28" height="18" rx="2" fill="none" stroke="#534AB7" stroke-width="2"/><rect x="12" y="10" width="8" height="10" rx="1" fill="none" stroke="#534AB7" stroke-width="1.5"/><circle cx="16" cy="27" r="1" fill="#534AB7"/></svg>`,
  wireframing: `<svg viewBox="0 0 32 32" width="20" height="20"><rect x="3" y="3" width="26" height="26" rx="2" fill="none" stroke="#D46A8A" stroke-width="2"/><line x1="3" y1="10" x2="29" y2="10" stroke="#D46A8A" stroke-width="1.5"/><rect x="6" y="14" width="8" height="6" rx="1" fill="none" stroke="#D46A8A" stroke-width="1.5"/><line x1="17" y1="15" x2="26" y2="15" stroke="#D46A8A" stroke-width="1.5"/><line x1="17" y1="19" x2="26" y2="19" stroke="#D46A8A" stroke-width="1.5"/></svg>`,
  prototyping: `<svg viewBox="0 0 32 32" width="20" height="20"><circle cx="8" cy="8" r="4" fill="none" stroke="#D46A8A" stroke-width="1.5"/><circle cx="24" cy="8" r="4" fill="none" stroke="#D46A8A" stroke-width="1.5"/><circle cx="8" cy="24" r="4" fill="none" stroke="#D46A8A" stroke-width="1.5"/><circle cx="24" cy="24" r="4" fill="none" stroke="#D46A8A" stroke-width="1.5"/><line x1="12" y1="8" x2="20" y2="8" stroke="#D46A8A" stroke-width="1.5"/><line x1="8" y1="12" x2="8" y2="20" stroke="#D46A8A" stroke-width="1.5"/><line x1="12" y1="24" x2="20" y2="24" stroke="#D46A8A" stroke-width="1.5"/><line x1="24" y1="12" x2="24" y2="20" stroke="#D46A8A" stroke-width="1.5"/></svg>`,
  restapi: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="none" stroke="#639922" stroke-width="2" d="M4 16h6m12 0h6M10 16a6 6 0 0012 0 6 6 0 00-12 0z"/><circle cx="16" cy="16" r="2" fill="#639922"/></svg>`,
  github: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#24292E" d="M16 3C8.8 3 3 8.8 3 16c0 5.7 3.7 10.6 8.9 12.3.6.1.9-.3.9-.6v-2.1c-3.6.8-4.4-1.7-4.4-1.7-.6-1.4-1.4-1.8-1.4-1.8-1.1-.8.1-.8.1-.8 1.3.1 1.9 1.3 1.9 1.3 1.1 1.9 2.9 1.3 3.6 1 .1-.8.4-1.3.8-1.6-2.8-.3-5.7-1.4-5.7-6.2 0-1.4.5-2.5 1.3-3.4-.1-.3-.6-1.6.1-3.3 0 0 1.1-.3 3.5 1.3a12 12 0 016.4 0c2.4-1.6 3.5-1.3 3.5-1.3.7 1.7.3 3 .1 3.3.8.9 1.3 2 1.3 3.4 0 4.8-2.9 5.9-5.7 6.2.4.4.8 1.1.8 2.2v3.3c0 .3.2.7.9.6C25.3 26.6 29 21.7 29 16c0-7.2-5.8-13-13-13z"/></svg>`,
  vscode: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#0078D7" d="M23.5 3.8L13 14.3l-6-5L4 11l6 5-6 5 3 2.2 6-5 10.5 10.5 4.5-2V5.8l-4.5-2zM24 9.5v13L17.5 16 24 9.5z"/></svg>`,
  vercel: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#000" d="M16 3C8.8 3 3 8.8 3 16s5.8 13 13 13 13-5.8 13-13S23.2 3 16 3zm0 2.5c5.7 0 10.5 4.8 10.5 10.5s-4.8 10.5-10.5 10.5-10.5-4.8-10.5-10.5S10.3 5.5 16 5.5z"/><path fill="#fff" d="M16 9c-4.4 0-8 3.6-8 8s3.6 8 8 8h4v-4h-4c-4.4 0-8-3.6-8-8s3.6-8 8-8z"/></svg>`,
  apidog: `<svg viewBox="0 0 32 32" width="20" height="20"><path fill="#000" d="M16 3C8.8 3 3 8.8 3 16s5.8 13 13 13 13-5.8 13-13S23.2 3 16 3zm0 2.5c5.7 0 10.5 4.8 10.5 10.5s-4.8 10.5-10.5 10.5-10.5-4.8-10.5-10.5S10.3 5.5 16 5.5z"/><path fill="#000" d="M21.7 12H18v-1h6v1zm0 4h-6v-1h6v1z"/></svg>`,
}
  const skillCategories = [
  {
    title: 'Frontend',
    icon: IconCode,
    iconBg: '#EEEDFE',
    iconColor: '#534AB7',
    skills: [
      { name: 'HTML & CSS',  logo: logos.html + logos.css },
      { name: 'Next.js',     logo: logos.next },
      { name: 'Vue.js',      logo: logos.vue },
      { name: 'React.js',    logo: logos.react },
    ],
  },
  {
    title: 'UI/UX Design',
    icon: IconPalette,
    iconBg: '#FBEAF0',
    iconColor: '#8B1A3E',
    skills: [
      { name: 'Figma',             logo: logos.figma },
      { name: 'Responsive Design', logo: logos.responsivedesign },
      { name: 'Wireframing',       logo: logos.wireframing },
      { name: 'Prototyping',       logo: logos.prototyping },
    ],
  },
  {
    title: 'Backend & Other',
    icon: IconServer,
    iconBg: '#EAF3DE',
    iconColor: '#3B6D11',
    skills: [
      { name: 'Node.js',    logo: logos.node },
      { name: 'NestJS',     logo: logos.nestjs },
      { name: 'Spring Boot',logo: logos.springboot },
      { name: 'REST API',   logo: logos.restapi },
    ],
  },
]

const tools = [
  { name: 'Git',     bg: '#FFF0EB', color: '#8B2500', border: '#F4C4B3', logo: logos.git },
  { name: 'GitHub',  bg: '#F4F4F4', color: '#24292E', border: '#D0D7DE', logo: logos.github },
  { name: 'Figma',   bg: '#FBEAF0', color: '#8B1A3E', border: '#F4C0D1', logo: logos.figma },
  { name: 'VS Code', bg: '#E6F1FB', color: '#185FA5', border: '#B5D4F4', logo: logos.vscode },
  { name: 'Flutter', bg: '#EAF3FE', color: '#0d4a8a', border: '#B5D4F4', logo: logos.flutter },
  { name: 'Vercel', bg: '#E6F7F0', color: '#1a6645', border: '#9FE1CB', logo: logos.vercel },
  { name: 'API Dog', bg: '#FFF4E8', color: '#8B4A00', border: '#FAC775', logo: logos.apidog },
]
</script>

<style scoped>
.skills-section {
  padding: 100px 0;
  background: var(--bg);
  border-top: 1px solid var(--border);
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
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 40px;
}
.skill-category {
  padding: 24px;
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  background: var(--surface);
  transition: border-color 0.2s, transform 0.2s;
}
.skill-category:hover {
  border-color: var(--purple-200);
  transform: translateY(-3px);
}
.category-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}
.category-icon {
  width: 38px;
  height: 38px;
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.category-title {
  font-size: 15px;
  font-weight: 500;
  color: var(--text-primary);
  font-family: 'DM Sans', sans-serif;
}
.skill-list { display: flex; flex-direction: column; gap: 10px; }
.skill-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 9px 12px;
  border-radius: var(--radius-md);
  border: 1px solid var(--border);
  background: var(--bg);
  transition: border-color 0.2s, transform 0.15s;
}
.skill-item:hover {
  border-color: var(--purple-200);
  transform: translateX(4px);
}
.skill-logo {
  display: flex;
  align-items: center;
  gap: 3px;
  flex-shrink: 0;
}
.skill-logo :deep(svg) { border-radius: 3px; }
.skill-name {
  font-size: 13px;
  color: var(--text-primary);
  font-weight: 400;
}
.tools-row {
  padding: 28px;
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  background: var(--surface);
}
.tools-label {
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 16px;
}
.tools-tags { display: flex; flex-wrap: wrap; gap: 8px; }
.tool-tag {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  font-weight: 500;
  padding: 6px 13px;
  border-radius: 20px;
  border: 1px solid;
  transition: transform 0.2s;
}
.tool-tag:hover { transform: translateY(-2px); }
.tool-logo { display: flex; align-items: center; }
.tool-logo :deep(svg) { border-radius: 3px; }

@media (max-width: 900px) { .skills-grid { grid-template-columns: 1fr 1fr; } }
@media (max-width: 600px) { .skills-grid { grid-template-columns: 1fr; } }
</style>