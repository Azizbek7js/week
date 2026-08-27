<script setup>
const exportTypes = [
  { label: 'IT Services', value: '53%' },
  { label: 'Software Products', value: '8%' },
  { label: 'BPO', value: '28%' },
  { label: 'Creative & GameDev', value: '11%' }
]
const geography = [
  { label: 'NORTH AMERICA', value: '46%' },
  { label: 'CIS & APAC', value: '27%' },
  { label: 'EU AND UK', value: '21%' },
  { label: 'MENA', value: '6%' }
]
const offices = ['USA', 'Germany', 'Saudi Arabia', 'China', 'South Korea', 'Japan']
const bigStats = [
  { title: 'Number of Member Companies', value: '3 400+', growth: '22x', note: 'increase' },
  { title: 'Growth of Companies with Foreign Capital', value: '970+', growth: '127x', note: 'increase', extra: 'Number of American capital companies' },
  { title: 'Revenue of Members (Million USD)', value: '2 800.0', growth: '127x', note: 'increase' }
]
</script>

<template>
  <section class="section indicators">
    <div class="container">
      <div class="indicators__panel">
        <div class="indicators__head">
          <span class="indicators__bar" aria-hidden="true"></span>
          <h2>KEY INDICATORS OF IT PARK MEMBERS</h2>
        </div>

        <div class="indicators__row indicators__row--top">
          <div class="indicators__box indicators__box--geo">
            <h3>EXPORT GEOGRAPHY</h3>
            <ul>
              <li v-for="g in geography" :key="g.label">
                <strong>{{ g.value }}</strong>
                <span>{{ g.label }}</span>
              </li>
            </ul>
          </div>

          <div class="indicators__box">
            <h3>Types of Export</h3>
            <div class="indicators__donut" aria-hidden="true">
              <span>$1B</span>
            </div>
            <ul class="indicators__export-list">
              <li v-for="e in exportTypes" :key="e.label">
                <strong>{{ e.value }}</strong> {{ e.label }}
              </li>
            </ul>
          </div>

          <div class="indicators__box">
            <h3>ICT Export Revenue <small>(Million USD)</small></h3>
            <p class="indicators__growth"><strong>7.2x</strong> increase</p>
            <div class="indicators__bars">
              <div class="indicators__bar-item" style="--h: 20%"><span>151</span></div>
              <div class="indicators__bar-item" style="--h: 35%"><span>18</span></div>
              <div class="indicators__bar-item" style="--h: 70%"><span>540</span></div>
              <div class="indicators__bar-item" style="--h: 100%"><span>1110</span></div>
            </div>
            <div class="indicators__years">
              <span>2017</span><span>2021</span><span>2023</span><span>YTD 2025</span>
            </div>
          </div>
        </div>

        <div class="indicators__offices">
          <h3>6 REPRESENTATIVE OFFICES ABROAD</h3>
          <ul>
            <li v-for="o in offices" :key="o">{{ o }}</li>
          </ul>
        </div>

        <div class="indicators__row indicators__row--bottom">
          <div v-for="s in bigStats" :key="s.title" class="indicators__box">
            <h3>{{ s.title }}</h3>
            <p class="indicators__growth"><strong>{{ s.growth }}</strong> increase</p>
            <p v-if="s.extra" class="indicators__extra">{{ s.extra }}</p>
            <div class="indicators__bars">
              <div class="indicators__bar-item" style="--h: 15%"><span></span></div>
              <div class="indicators__bar-item" style="--h: 35%"><span></span></div>
              <div class="indicators__bar-item" style="--h: 65%"><span></span></div>
              <div class="indicators__bar-item" style="--h: 100%"><span>{{ s.value }}</span></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.indicators__panel {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  background: var(--panel);
}
.indicators__head {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 22px;
}
.indicators__bar {
  width: 4px;
  height: 22px;
  background: linear-gradient(180deg, var(--accent-2), var(--accent));
  border-radius: 2px;
}
.indicators__head h2 {
  font-size: 18px;
  margin: 0;
  letter-spacing: 0.02em;
}

.indicators__row {
  display: grid;
  grid-template-columns: 1.3fr 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}
.indicators__row--bottom {
  grid-template-columns: repeat(3, 1fr);
}

.indicators__box {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
}
.indicators__box h3 {
  font-size: 14px;
  margin: 0 0 12px;
  color: var(--text-dim);
}
.indicators__box h3 small {
  color: var(--text-faint);
  font-weight: 400;
}

.indicators__box--geo ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.indicators__box--geo li strong {
  display: block;
  color: var(--accent-2);
  font-size: 18px;
}
.indicators__box--geo li span {
  font-size: 11px;
  color: var(--text-faint);
}

.indicators__donut {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  margin: 0 auto 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: conic-gradient(var(--accent) 0 53%, #4a9c7a 53% 61%, #2a4438 61% 89%, #1c2e26 89% 100%);
  position: relative;
}
.indicators__donut::after {
  content: '';
  position: absolute;
  inset: 14px;
  border-radius: 50%;
  background: var(--panel);
}
.indicators__donut span {
  position: relative;
  z-index: 1;
  font-weight: 800;
  font-size: 14px;
}
.indicators__export-list {
  list-style: none;
  margin: 0;
  padding: 0;
  font-size: 12px;
  color: var(--text-dim);
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.indicators__export-list strong {
  color: var(--accent-2);
}

.indicators__growth {
  margin: 0 0 10px;
  font-size: 13px;
  color: var(--text-dim);
}
.indicators__growth strong {
  color: var(--accent-2);
  font-size: 20px;
  margin-right: 4px;
}
.indicators__extra {
  font-size: 11px;
  color: var(--accent-2);
  margin: -6px 0 10px;
}
.indicators__bars {
  display: flex;
  align-items: flex-end;
  gap: 8px;
  height: 90px;
}
.indicators__bar-item {
  flex: 1;
  height: var(--h);
  background: linear-gradient(180deg, var(--accent-2), rgba(62, 224, 138, 0.25));
  border-radius: 6px 6px 0 0;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  position: relative;
}
.indicators__bar-item span {
  position: absolute;
  top: -18px;
  font-size: 10px;
  color: var(--text-dim);
  white-space: nowrap;
}
.indicators__years {
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: var(--text-faint);
  margin-top: 8px;
}

.indicators__offices {
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 16px 18px;
  margin-bottom: 16px;
  background: rgba(255, 255, 255, 0.02);
}
.indicators__offices h3 {
  font-size: 13px;
  margin: 0 0 12px;
  color: var(--text-dim);
  text-align: center;
}
.indicators__offices ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  font-size: 13px;
  color: var(--text-dim);
}

@media (max-width: 1024px) {
  .indicators__row,
  .indicators__row--bottom {
    grid-template-columns: 1fr 1fr;
  }
}
@media (max-width: 640px) {
  .indicators__panel {
    padding: 18px;
  }
  .indicators__row,
  .indicators__row--bottom {
    grid-template-columns: 1fr;
  }
  .indicators__box--geo ul {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
