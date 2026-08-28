<script setup>
import Sandbox from '../assets/images/Sandbox.webp'
import exchange from '../assets/images/currency-exchange.webp'
import taxRefund from '../assets/images/tax-refund.webp'
import fileFolder from '../assets/images/file-folder.webp'
import databaseConnection from '../assets/images/database-connection.webp'
import Government from '../assets/images/services.webp'
import digitalBrain from '../assets/images/digital-brain.webp'
import earningsReport from '../assets/images/earnings-report.webp'
import globalNetwork from '../assets/images/global-network.webp'

const features = [
  { title: 'Regulatory Sandbox', desc: 'Legally protected testing environment for new business models and frontier technologies.' },
  { title: 'Foreign exchange freedom', desc: 'Foreign currency operations, payroll, and capital flows without conversion mandates.' },
  { title: 'Tax & customs', desc: 'Corporate tax exemption for export-led companies; customs-duty exemption on equipment imports.' },
  { title: 'Labour relations', desc: 'International-grade employment structures aligned with global labour standards.' },
  { title: 'Personal data', desc: 'Internationally aligned data protection rules with full support for cross-border processing.' },
  { title: 'Government services', desc: 'Full government services for foreign residents — including remote registration and licensing.' },
  { title: 'Intellectual property', desc: 'Enhanced IP protections with specific provisions for AI-generated outputs and software assets.' },
  { title: 'Investment attraction', desc: 'Investment instruments purpose-built for venture financing — SAFEs, convertibles, hybrid structures.' },
  { title: 'Export promotion', desc: 'Favourable operating conditions for export-driven companies with zero-friction outbound trade.' }
]
</script>

<template>
  <section class="section features">
    <div class="container">
      <div class="features__panel">
        <div class="features__head">
          <span class="features__bar" aria-hidden="true"></span>
          <h2>ENTERPRISE UZBEKISTAN</h2>
        </div>
        <div class="features__grid">
          <article v-for="f in features" :key="f.title" class="features__card">
            <h3>{{ f.title }}</h3>
            <p>{{ f.desc }}</p>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.features__panel {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  background: var(--panel);
}
.features__head {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 22px;
}
.features__bar {
  width: 4px;
  height: 22px;
  background: linear-gradient(180deg, var(--accent-2), var(--accent));
  border-radius: 2px;
}
.features__head h2 {
  font-size: 18px;
  margin: 0;
}
.features__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.features__card {
  background: linear-gradient(160deg, rgba(62, 224, 138, 0.07), rgba(255, 255, 255, 0.015));
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 20px;
}
.features__card h3 {
  font-size: 17px;
  margin: 0 0 10px;
}
.features__card p {
  font-size: 13px;
  color: var(--text-dim);
  line-height: 1.5;
  margin: 0;
}

@media (max-width: 1024px) {
  .features__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (max-width: 640px) {
  .features__panel {
    padding: 18px;
  }
  .features__grid {
    grid-template-columns: 1fr;
  }
}
</style>
