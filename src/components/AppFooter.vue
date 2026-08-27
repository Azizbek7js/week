<script setup>
const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="container footer__inner">
      <a href="#top" class="footer__logo">
        <span class="footer__logo-dots" aria-hidden="true"><i></i><i></i><i></i></span>
        ictweek
      </a>
      <p>© {{ year }} ICT Week Uzbekistan. All rights reserved.</p>
      <nav class="footer__links" aria-label="Footer">
        <a href="#top">Home</a>
        <a href="#tracks">Program</a>
        <a href="#register">Register</a>
      </nav>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  padding: 28px 0;
}
.footer__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 14px;
}
.footer__logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  color: var(--text);
  font-weight: 700;
  font-size: 14px;
}
.footer__logo-dots {
  position: relative;
  width: 20px;
  height: 20px;
  display: inline-block;
}
.footer__logo-dots i {
  position: absolute;
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: var(--accent);
}
.footer__logo-dots i:nth-child(1) { left: 0; top: 8px; }
.footer__logo-dots i:nth-child(2) { left: 8px; top: 0; }
.footer__logo-dots i:nth-child(3) { left: 8px; top: 16px; }

.footer p {
  color: var(--text-faint);
  font-size: 12.5px;
  margin: 0;
}
.footer__links {
  display: flex;
  gap: 18px;
}
.footer__links a {
  color: var(--text-dim);
  text-decoration: none;
  font-size: 13px;
}
.footer__links a:hover {
  color: var(--accent-2);
}

@media (max-width: 640px) {
  .footer__inner {
    flex-direction: column;
    text-align: center;
  }
}
</style>
