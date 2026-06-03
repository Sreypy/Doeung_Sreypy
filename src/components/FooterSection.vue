<template>
  <footer class="footer">
    <div class="container footer-inner">
      <p class="footer-brand">Doeung Sreypy</p>
      <p class="footer-sub">Web Developer & UI/UX Designer</p>
      <p class="footer-tag">Passionate about creating exceptional digital experiences</p>
      <p class="footer-copy">© {{ year }} Doeung Sreypy</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  padding: 48px 0;
  border-top: 1px solid var(--border);
  text-align: center;
}
.footer-brand {
  font-family: 'DM Serif Display', serif;
  font-size: 20px;
  color: var(--text-primary);
  margin-bottom: 4px;
}
.footer-sub {
  font-size: 13px;
  color: var(--purple-500);
  margin-bottom: 12px;
  font-weight: 500;
}
.footer-tag {
  font-size: 13px;
  color: var(--text-muted);
  font-weight: 300;
  margin-bottom: 8px;
}
.footer-copy { font-size: 12px; color: var(--text-muted); }
</style>
