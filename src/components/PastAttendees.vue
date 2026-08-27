<script setup>
const logos = [
  'web summit', 'Plug and Play', 'MIT', 'Google for Startups', 'AWS',
  'Alchemist Accelerator', 'dealroom.co', 'StartupBlink', 'DOMINO', 'Startup Genome',
  'accesa', 'Sturgeon Capital', 'salesforce.org', 'EY', 'Global Startup Awards',
  'GBTP', 'Polyvalent', 'Golden Gate Ventures', 'SPS Commerce'
]
</script>

<template>
  <section class="section attendees">
    <div class="container">
      <h2 class="attendees__title">Past Attendees Include</h2>
      <ul class="attendees__grid">
        <li v-for="logo in logos" :key="logo" class="attendees__logo">
          {{ logo }}
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.attendees {
  background: radial-gradient(60% 60% at 50% 0%, rgba(62, 224, 138, 0.08), transparent 70%);
}
.attendees__title {
  text-align: center;
  font-size: 32px;
  margin: 0 0 32px;
}
.attendees__grid {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 16px;
}
.attendees__logo {
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  background: rgba(255, 255, 255, 0.02);
  min-height: 76px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 10px;
  font-weight: 700;
  font-size: 13px;
  color: var(--text-dim);
  text-transform: uppercase;
  letter-spacing: 0.02em;
}

@media (max-width: 1024px) {
  .attendees__grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
@media (max-width: 640px) {
  .attendees__grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .attendees__title {
    font-size: 24px;
  }
}
</style>
