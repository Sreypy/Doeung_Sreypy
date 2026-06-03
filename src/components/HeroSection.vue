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
          <!-- Subtle glow behind card -->
          <div class="glow-ring"></div>

          <!-- Formal card frame -->
          <div class="avatar-float">
            <div class="avatar-card">
              <div class="avatar-card-inner">
                <img src="/profile.jpg" alt="Doeung Sreypy" class="profile-img" />
                <!-- Name plate at bottom -->
                <div class="name-plate">
                  <p class="name-plate-name">Doeung Sreypy</p>
                  <p class="name-plate-role">Web Developer · UI/UX</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Decorative corner accents -->
          <div class="corner corner-tl"></div>
          <div class="corner corner-tr"></div>
          <div class="corner corner-bl"></div>
          <div class="corner corner-br"></div>
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

/* ── Text animations ── */
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

/* ── Typewriter ── */
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

.hero-title {
  font-size: clamp(36px, 5vw, 56px);
  color: var(--text-primary);
  margin-bottom: 20px;
  letter-spacing: -0.03em;
}
.hero-name { color: var(--purple-500); font-style: italic; }
.hero-desc {
  font-size: 16px;
  color: var(--text-secondary);
  line-height: 1.75;
  max-width: 440px;
  margin-bottom: 32px;
  font-weight: 300;
}

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
  width: 260px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Subtle glow behind */
.glow-ring {
  position: absolute;
  inset: -24px;
  border-radius: 20px;
  background: radial-gradient(circle, rgba(83,74,183,0.12) 0%, transparent 70%);
  animation: glowPulse 4s ease-in-out infinite;
  pointer-events: none;
}
@keyframes glowPulse {
  0%, 100% { opacity: 0.6; transform: scale(1); }
  50%       { opacity: 1;   transform: scale(1.04); }
}

/* Formal card frame */
.avatar-float {
  animation: floatUpDown 5s ease-in-out infinite;
  width: 100%;
}
@keyframes floatUpDown {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(-10px); }
}

.avatar-card {
  border-radius: 16px;
  padding: 6px;
  background: linear-gradient(145deg, var(--purple-200), rgba(175,169,236,0.3), var(--purple-200));
  box-shadow:
    0 20px 60px rgba(83,74,183,0.2),
    0 4px 16px rgba(83,74,183,0.1);
}

.avatar-card-inner {
  border-radius: 16px;
  overflow: hidden;
  background: var(--surface);
  position: relative;
}

.profile-img {
  width: 100%;
  height: 290px;
  object-fit: cover;
  object-position: center 5%;
  display: block;
  filter: contrast(1.02) brightness(1.01);
}

/* Name plate */
.name-plate {
  padding: 14px 16px;
  background: var(--surface);
  border-top: 1px solid var(--border);
  text-align: center;
}
.name-plate-name {
  font-size: 14px;
  font-weight: 500;
  color: var(--text-primary);
  font-family: 'DM Serif Display', serif;
  margin-bottom: 2px;
}
.name-plate-role {
  font-size: 11px;
  color: var(--purple-500);
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

/* Decorative corner accents */
.corner {
  position: absolute;
  width: 16px;
  height: 16px;
  border-color: var(--purple-500);
  border-style: solid;
  opacity: 0.5;
}
.corner-tl { top: -6px; left: -6px; border-width: 2px 0 0 2px; border-radius: 3px 0 0 0; }
.corner-tr { top: -6px; right: -6px; border-width: 2px 2px 0 0; border-radius: 0 3px 0 0; }
.corner-bl { bottom: -6px; left: -6px; border-width: 0 0 2px 2px; border-radius: 0 0 0 3px; }
.corner-br { bottom: -6px; right: -6px; border-width: 0 2px 2px 0; border-radius: 0 0 3px 0; }

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
  .avatar-wrapper { width: 200px; }
  .profile-img { height: 260px; }
}
</style>