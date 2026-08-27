<script setup>
const items = [
  { value: '100%', label: 'Reimbursement for patenting and trademark registration' },
  { value: '', icon: 'shield', label: 'Special legal regime "Regulatory Sandbox" for rapid piloting' },
  { value: '$50K', label: 'Reimbursement for mentor/trainer costs in acceleration programs' },
  { value: '1+1', label: 'Co-funding mechanism matching foreign investment dollar-for-dollar' },
  { value: '$20K', label: 'Reimbursement of international acceleration program costs' },
  { value: '1 YEAR', label: 'Free access to the massive Digital Data Platform for Startups' },
  { value: '1 YEAR', label: 'Free dedicated legal and financial consultations with top experts' },
  { value: '$10K', label: 'Awarding grants directly to winners of national hackathons and ideathons' }
]
</script>

<template>
  <section class="section startups">
    <div class="container">
      <div class="startups__panel">
        <div class="startups__head">
          <span class="startups__bar" aria-hidden="true"></span>
          <h2>DIGITAL STARTUPS PROGRAM</h2>
        </div>

        <div class="startups__grid">
          <div v-for="(item, i) in items" :key="i" class="startups__item">
            <span v-if="item.value" class="startups__value">{{ item.value }}</span>
            <span v-else class="startups__icon" aria-hidden="true">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M12 3l7 3v6c0 4.5-3 7.5-7 9-4-1.5-7-4.5-7-9V6l7-3z" stroke="var(--accent)" stroke-width="1.6" /></svg>
            </span>
            <p>{{ item.label }}</p>
          </div>
        </div>

        <div class="startups__footer">
          <p>
            Digital Startups Program – a <strong>$50 million</strong> initiative, launched for
            promising Uzbek tech startups. Funding, mentorship, intellectual property protection
            and access to the global market — all available on one platform –
            <strong>startupbase.uz</strong>
          </p>
          <div class="startups__qr" role="img" aria-label="QR code to Startup Base platform"></div>
        </div>

        <div class="startups__nav">
          <button type="button" aria-label="Previous">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M15 5l-7 7 7 7" stroke="currentColor" stroke-width="2" stroke-linecap="round" /></svg>
          </button>
          <span>DIGITAL STARTUPS PROGRAM</span>
          <button type="button" aria-label="Next">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M9 5l7 7-7 7" stroke="#062015" stroke-width="2" stroke-linecap="round" /></svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.startups__panel {
  border: 1px solid var(--border-strong);
  border-radius: var(--radius-lg);
  padding: 28px;
  background: linear-gradient(160deg, rgba(62, 224, 138, 0.08), var(--panel) 60%);
}
.startups__head {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 22px;
}
.startups__bar {
  width: 4px;
  height: 22px;
  background: linear-gradient(180deg, var(--accent-2), var(--accent));
  border-radius: 2px;
}
.startups__head h2 {
  font-size: 17px;
  margin: 0;
}

.startups__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 14px;
  margin-bottom: 20px;
}
.startups__item {
  display: flex;
  align-items: center;
  gap: 14px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 14px 16px;
}
.startups__value {
  font-size: 20px;
  font-weight: 800;
  color: var(--accent-2);
  min-width: 64px;
}
.startups__icon {
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 64px;
}
.startups__item p {
  margin: 0;
  font-size: 12.5px;
  color: var(--text-dim);
  line-height: 1.4;
}

.startups__footer {
  display: flex;
  align-items: center;
  gap: 20px;
  background: linear-gradient(120deg, rgba(62, 224, 138, 0.16), rgba(62, 224, 138, 0.05));
  border-radius: var(--radius-md);
  padding: 18px 22px;
  margin-bottom: 18px;
}
.startups__footer p {
  margin: 0;
  font-size: 13px;
  color: var(--text);
  line-height: 1.5;
}
.startups__qr {
  width: 68px;
  height: 68px;
  flex-shrink: 0;
  border-radius: 8px;
  background:
    repeating-conic-gradient(#0b120f 0% 25%, #d7ffe9 0% 50%) 0 0/10px 10px;
}

.startups__nav {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
}
.startups__nav span {
  font-size: 13px;
  font-weight: 600;
  color: var(--text-dim);
}
.startups__nav button {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  border: 1px solid var(--border);
  background: transparent;
  color: var(--text-dim);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}
.startups__nav button:last-child {
  background: var(--accent);
  border-color: var(--accent);
}

@media (max-width: 640px) {
  .startups__panel {
    padding: 18px;
  }
  .startups__grid {
    grid-template-columns: 1fr;
  }
  .startups__footer {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
