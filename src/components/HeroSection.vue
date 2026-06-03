<template>
  <section id="home" class="hero">
    <div class="hero-bg-blob blob-1"></div>
    <div class="hero-bg-blob blob-2"></div>
    <div class="container hero-inner">

      <div class="hero-text">
        <p class="hero-eyebrow anim-slide-up" style="animation-delay: 0.1s">Web Developer · UI/UX Designer</p>
        <h1 class="hero-title anim-slide-up" style="animation-delay: 0.25s">
          Hello, I'm<br>
          <em class="hero-name">
            <span class="typewriter">Doeung Sreypy</span>
          </em>
        </h1>
        <p class="hero-desc anim-slide-up" style="animation-delay: 0.4s">
          Passionate about designing and building responsive websites with expertise in HTML, CSS, and JavaScript.
          I focus on delivering seamless user experiences across all devices.
        </p>
        <div class="hero-ctas anim-slide-up" style="animation-delay: 0.55s">
          <a href="#portfolio" class="btn btn-primary">View My Projects</a>
          <a href="#contact" class="btn btn-ghost">Get In Touch</a>
        </div>
      </div>

      <div class="hero-visual anim-slide-left" style="animation-delay: 0.3s">
        <div class="avatar-wrapper">
          <div class="glow-ring"></div>
          <div class="rotate-ring"></div>
          <div class="rotate-ring-2"></div>
          <div class="orbit-track">
            <div class="orbit-dot orbit-dot-1"></div>
          </div>
          <div class="orbit-track-2">
            <div class="orbit-dot orbit-dot-2"></div>
          </div>
          <div class="avatar-float">
            <div class="avatar-circle">
              <img src="/profile.jpg" alt="Doeung Sreypy" class="profile-img" />
            </div>
          </div>
          <div class="badge badge-tl">UI/UX</div>
          <div class="badge badge-br">Dev</div>
        </div>

        <div class="floating-tags anim-slide-up" style="animation-delay: 0.7s">
          <span class="ftag ftag-html">HTML</span>
          <span class="ftag ftag-css">CSS</span>
          <span class="ftag ftag-js">JavaScript</span>
          <span class="ftag ftag-vue">Vue.js</span>
          <span class="ftag ftag-react">React.js</span>
          <span class="ftag ftag-node">Node.js</span>
          <span class="ftag ftag-git">Git</span>
          <span class="ftag ftag-figma">Figma</span>
          <span class="ftag ftag-flutter">Flutter</span>
          <span class="ftag ftag-ui">UI/UX</span>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* ── Base ── */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: 100px 0 60px;
}
.hero-bg-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.35;
  pointer-events: none;
}
.blob-1 { width: 500px; height: 500px; background: var(--purple-50); top: -100px; right: -100px; }
.blob-2 { width: 350px; height: 350px; background: var(--teal-50); bottom: 0; left: -80px; }

.hero-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 60px;
}

/* ── Text entry animations ── */
@keyframes slideUp {
  from { opacity: 0; transform: translateY(32px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes slideLeft {
  from { opacity: 0; transform: translateX(40px); }
  to   { opacity: 1; transform: translateX(0); }
}

.anim-slide-up {
  opacity: 0;
  animation: slideUp 0.7s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}
.anim-slide-left {
  opacity: 0;
  animation: slideLeft 0.7s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}

/* ── Typewriter on name ── */
.typewriter {
  display: inline-block;
  overflow: hidden;
  white-space: nowrap;
  border-right: 3px solid var(--purple-500);
  width: 0;
  animation:
    typing 1.4s steps(14, end) 0.6s forwards,
    blink  0.75s step-end 0.6s 6;
}
@keyframes typing {
  from { width: 0; }
  to   { width: 100%; }
}
@keyframes blink {
  0%, 100% { border-color: var(--purple-500); }
  50%       { border-color: transparent; }
}

/* ── Eyebrow shimmer ── */
.hero-eyebrow {
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--purple-500);
  margin-bottom: 16px;
  background: linear-gradient(90deg, var(--purple-500) 0%, var(--teal-500) 50%, var(--purple-500) 100%);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 3s linear 1s infinite, slideUp 0.7s cubic-bezier(0.22,1,0.36,1) 0.1s forwards;
}
@keyframes shimmer {
  to { background-position: 200% center; }
}

/* ── Title ── */
.hero-title {
  font-size: clamp(36px, 5vw, 56px);
  color: var(--text-primary);
  margin-bottom: 20px;
  letter-spacing: -0.03em;
}
.hero-name { color: var(--purple-500); font-style: italic; }

/* ── Desc ── */
.hero-desc {
  font-size: 16px;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 440px;
  margin-bottom: 32px;
  font-weight: 300;
}

/* ── Buttons ── */
.hero-ctas { display: flex; gap: 12px; flex-wrap: wrap; }
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  font-weight: 500;
  padding: 12px 24px;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.2s;
  font-family: 'DM Sans', sans-serif;
}
.btn-primary { background: var(--purple-500); color: #fff; border: 1.5px solid var(--purple-500); }
.btn-primary:hover { background: var(--purple-800); border-color: var(--purple-800); transform: translateY(-2px); box-shadow: 0 8px 20px rgba(83,74,183,0.3); }
.btn-ghost { background: transparent; color: var(--text-primary); border: 1.5px solid var(--border-md); }
.btn-ghost:hover { border-color: var(--purple-200); color: var(--purple-500); transform: translateY(-2px); }

/* ── Visual side ── */
.hero-visual {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
}
.avatar-wrapper {
  position: relative;
  width: 300px;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Glow pulse */
.glow-ring {
  position: absolute;
  inset: -16px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(83,74,183,0.18) 0%, transparent 70%);
  animation: glowPulse 3s ease-in-out infinite;
}
@keyframes glowPulse {
  0%, 100% { transform: scale(1); opacity: 0.6; }
  50%       { transform: scale(1.12); opacity: 1; }
}

/* Rotating rings */
.rotate-ring {
  position: absolute;
  inset: -14px;
  border-radius: 50%;
  border: 2px dashed var(--purple-200);
  animation: spinCW 10s linear infinite;
}
.rotate-ring-2 {
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  border: 1.5px dashed rgba(83,74,183,0.2);
  animation: spinCCW 14s linear infinite;
}
@keyframes spinCW  { to { transform: rotate(360deg); } }
@keyframes spinCCW { to { transform: rotate(-360deg); } }

/* Orbiting dots */
.orbit-track, .orbit-track-2 {
  position: absolute;
  inset: -14px;
  border-radius: 50%;
}
.orbit-track   { animation: spinCW  10s linear infinite; }
.orbit-track-2 { animation: spinCCW 7s linear infinite; }

.orbit-dot { position: absolute; border-radius: 50%; }
.orbit-dot-1 {
  width: 16px; height: 16px;
  background: var(--purple-500);
  top: -8px; left: calc(50% - 8px);
  box-shadow: 0 0 0 4px rgba(83,74,183,0.2), 0 0 12px rgba(83,74,183,0.5);
}
.orbit-dot-2 {
  width: 12px; height: 12px;
  background: var(--teal-500);
  bottom: -6px; left: calc(50% - 6px);
  box-shadow: 0 0 0 3px rgba(29,158,117,0.2), 0 0 10px rgba(29,158,117,0.5);
}

/* Float up/down */
.avatar-float { animation: floatUpDown 4s ease-in-out infinite; }
@keyframes floatUpDown {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(-12px); }
}

.avatar-circle {
  width: 260px;
  height: 260px;
  border-radius: 50%;
  overflow: hidden;
  background: var(--purple-50);
  border: 3px solid var(--purple-200);
  box-shadow: 0 0 0 8px rgba(83,74,183,0.06), 0 20px 48px rgba(83,74,183,0.2);
}
.profile-img {
  width: 100%;
  height: 110%;
  object-fit: cover;
  object-position: center 10%;
  display: block;
}

/* Corner badges */
.badge {
  position: absolute;
  font-size: 11px;
  font-weight: 600;
  padding: 5px 12px;
  border-radius: 20px;
  letter-spacing: 0.04em;
  animation: floatUpDown 4s ease-in-out infinite;
}
.badge-tl {
  top: 16px; left: -8px;
  background: var(--purple-50);
  color: var(--purple-800);
  border: 1px solid var(--purple-200);
  animation-delay: 0.5s;
}
.badge-br {
  bottom: 16px; right: -8px;
  background: #E6F7F0;
  color: #1a6645;
  border: 1px solid #9FE1CB;
  animation-delay: 1s;
}

/* Tags */
.floating-tags {
  display: flex;
  gap: 7px;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 340px;
}
.ftag {
  font-size: 11px;
  font-weight: 500;
  padding: 4px 11px;
  border-radius: 20px;
  border: 1px solid;
  transition: transform 0.2s;
}
.ftag:hover { transform: translateY(-2px); }
.ftag-html    { background: #FFF0EB; color: #C44B0A; border-color: #F4C4B3; }
.ftag-css     { background: #E6F1FB; color: #185FA5; border-color: #B5D4F4; }
.ftag-js      { background: #FAEEDA; color: #854F0B; border-color: #FAC775; }
.ftag-vue     { background: #E6F7F0; color: #1a6645; border-color: #9FE1CB; }
.ftag-react   { background: #E6F4FB; color: #0d5c7a; border-color: #85CCE8; }
.ftag-node    { background: #EAF3DE; color: #3B6D11; border-color: #C0DD97; }
.ftag-git     { background: #FFF0EB; color: #8B2500; border-color: #F4C4B3; }
.ftag-figma   { background: #FBEAF0; color: #8B1A3E; border-color: #F4C0D1; }
.ftag-flutter { background: #EAF3FE; color: #0d4a8a; border-color: #B5D4F4; }
.ftag-ui      { background: var(--purple-50); color: var(--purple-800); border-color: var(--purple-200); }

@media (max-width: 768px) {
  .hero-inner { grid-template-columns: 1fr; text-align: center; gap: 40px; }
  .hero-desc { margin: 0 auto 32px; }
  .hero-ctas { justify-content: center; }
  .hero-visual { order: -1; }
  .avatar-wrapper { width: 240px; height: 240px; }
  .avatar-circle { width: 210px; height: 210px; }
}
</style>