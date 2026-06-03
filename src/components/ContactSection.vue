<template>
  <section id="contact" class="contact-section">
    <div class="container">
      <div class="section-header">
        <p class="section-eyebrow">Let's Talk</p>
        <h2 class="section-title">Get In <em>Touch</em></h2>
        <p class="section-sub">Ready to start your next project? Let's bring your ideas to life.</p>
      </div>

      <div class="contact-grid">
        <div class="contact-info">
          <h3 class="info-title">Let's start a conversation</h3>
          <p class="info-text">I'm always excited to discuss new projects and opportunities. Whether you need a complete website, UI/UX design, or just want to brainstorm ideas, I'm here to help.</p>
          <div class="info-cards">
            <div class="info-card">
              <div class="info-icon">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                  <polyline points="22,6 12,13 2,6"/>
                </svg>
              </div>
              <div>
                <p class="ic-label">Email</p>
                <p class="ic-val">sreypydoeung27@gmail.com</p>
              </div>
            </div>
            <div class="info-card">
              <div class="info-icon">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                  <circle cx="12" cy="12" r="10"/>
                  <polyline points="12,6 12,12 16,14"/>
                </svg>
              </div>
              <div>
                <p class="ic-label">Response time</p>
                <p class="ic-val">Usually within 24 hours</p>
              </div>
            </div>
          </div>
        </div>

        <form class="contact-form" @submit.prevent="handleSubmit">
          <div class="form-row">
            <div class="form-group">
              <label for="name">Name</label>
              <input id="name" v-model="form.name" type="text" placeholder="Your name" required />
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input id="email" v-model="form.email" type="email" placeholder="your@email.com" required />
            </div>
          </div>
          <div class="form-group">
            <label for="subject">Subject</label>
            <input id="subject" v-model="form.subject" type="text" placeholder="What's this about?" required />
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" v-model="form.message" rows="5" placeholder="Tell me about your project..." required></textarea>
          </div>
          <button type="submit" class="submit-btn" :class="{ sent: submitted }">
            <svg v-if="!submitted" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="22" y1="2" x2="11" y2="13"/><polygon points="22,2 15,22 11,13 2,9 22,2"/>
            </svg>
            <svg v-else width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="20,6 9,17 4,12"/>
            </svg>
            {{ submitted ? 'Message Sent!' : 'Send Message' }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({ name: '', email: '', subject: '', message: '' })
const submitted = ref(false)

function handleSubmit() {
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    Object.assign(form, { name: '', email: '', subject: '', message: '' })
  }, 3000)
}
</script>

<style scoped>
.contact-section {
  padding: 100px 0;
  background: var(--surface);
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

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 60px;
  align-items: start;
}
.info-title {
  font-size: 18px;
  font-weight: 500;
  color: var(--text-primary);
  margin-bottom: 12px;
  font-family: 'DM Serif Display', serif;
}
.info-text {
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.75;
  font-weight: 300;
  margin-bottom: 28px;
}
.info-cards { display: flex; flex-direction: column; gap: 12px; }
.info-card {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px 16px;
  border-radius: var(--radius-md);
  border: 1px solid var(--border);
  background: var(--bg);
}
.info-icon {
  width: 36px;
  height: 36px;
  border-radius: var(--radius-sm);
  background: var(--purple-50);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--purple-500);
  flex-shrink: 0;
}
.ic-label { font-size: 11px; color: var(--text-muted); margin-bottom: 2px; }
.ic-val { font-size: 13px; color: var(--text-primary); font-weight: 400; }

.contact-form { display: flex; flex-direction: column; gap: 14px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
.form-group { display: flex; flex-direction: column; gap: 6px; }
label { font-size: 12px; color: var(--text-secondary); font-weight: 500; letter-spacing: 0.02em; }
input, textarea {
  padding: 10px 14px;
  border-radius: var(--radius-md);
  border: 1px solid var(--border-md);
  background: var(--bg);
  color: var(--text-primary);
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 300;
  transition: border-color 0.2s, box-shadow 0.2s;
  outline: none;
  resize: none;
}
input:focus, textarea:focus {
  border-color: var(--purple-200);
  box-shadow: 0 0 0 3px rgba(83,74,183,0.08);
}
input::placeholder, textarea::placeholder { color: var(--text-muted); }

.submit-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 13px 28px;
  border-radius: 50px;
  border: none;
  background: var(--purple-500);
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  font-family: 'DM Sans', sans-serif;
  cursor: pointer;
  transition: background 0.2s, transform 0.2s;
}
.submit-btn:hover { background: var(--purple-800); transform: translateY(-1px); }
.submit-btn.sent { background: var(--teal-500); }

@media (max-width: 768px) {
  .contact-grid { grid-template-columns: 1fr; gap: 40px; }
  .form-row { grid-template-columns: 1fr; }
}
</style>
