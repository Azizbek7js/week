<script setup>
const partners = ['aws', 'StartupBlink', 'Startup World Cup', 'DIFC Innovation Hub', 'Pegasus Tech Ventures', 'JETRO', 'IGNYTE']
</script>

<template>
  <section class="section partners">
    <div class="container">
      <div class="partners__panel">
        <h2>Our Partners</h2>
        <ul class="partners__grid">
          <li v-for="p in partners" :key="p">{{ p }}</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.partners__panel {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 32px;
  background: var(--panel);
  text-align: center;
}
.partners__panel h2 {
  font-size: 24px;
  margin: 0 0 24px;
}
.partners__grid {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 14px;
}
.partners__grid li {
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  min-height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 13px;
  color: var(--text-dim);
  padding: 10px;
  text-align: center;
}

@media (max-width: 768px) {
  .partners__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
