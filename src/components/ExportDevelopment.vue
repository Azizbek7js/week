<script setup>
import FreeOfficeIcon from '../assets/images/FreeOffice.svg'
import Technical from '../assets/images/Technical.svg'
import farmImage from '../assets/images/farmImage.svg'
import RegistrationIcon from '../assets/images/Registration.svg'
import Banking from '../assets/images/Banking.svg'
import Turnkey from '../assets/images/Turnkey.svg'
import Talent from '../assets/images/Talent.svg'
import ITVISALOGO from '../assets/images/it-visa.svg'
import noWork from '../assets/images/noWork.svg'
import salary from '../assets/images/salary.svg'
import Dividends from '../assets/images/Dividends.svg'
import datavoltlogo from '../assets/images/datavoltlogo.png'

const benefits = [
  { label: 'CORPORATE TAXES', value: '0%' },
  { label: 'SOCIAL TAX', value: '0%' },
  { label: 'PROPERTY & LAND TAX', value: '0%' },
  { label: 'VAT ON IMPORTED SERVICES', value: 'NO' },
  { label: 'TAX ON DIVIDENDS', value: '5%' },
  { label: 'PERSONAL INCOME TAX', value: '7.5%' }
]
const softlanding = ['3 days Company registration', 'Banking support', 'Turnkey Accounting and Legal Services', 'Talent and Staff Recruitment']
const itVisa = ['No work permit', 'Salary in foreign currency', 'Dividends in foreign currency']
</script>

<template>
  <section class="section export">
    <div class="container">
      <div class="export__panel">
        <div class="export__head">
          <span class="export__bar" aria-hidden="true"></span>
          <h2>DIGITAL SERVICE AND PRODUCTS EXPORT DEVELOPMENT</h2>
        </div>

        <div class="export__grid">
          <div class="export__box">
            <h3>BENEFITS FOR IT PARK MEMBER COMPANIES</h3>
            <ul class="export__benefits">
              <li v-for="b in benefits" :key="b.label">
                <strong>{{ b.value }}</strong>
                <span>{{ b.label }}</span>
              </li>
            </ul>
          </div>

          <div class="export__box">
            <h3>ZERO RISK EXPENSE REIMBURSEMENT</h3>
            <div class="export__reimburse">
              <p>Free office for 1 year</p>
              <p>Technical Equipment for 1 year</p>
            </div>
          </div>

          <div class="export__box export__box--energy">
            <div class="export__energy-map" role="img" aria-label="Map of Uzbekistan"></div>
            <div class="export__energy-stats">
              <p><strong>9.3 GW</strong><span>Major green, wind-powered energy capacity</span><em>Wind farms</em></p>
              <p><strong>1 885 km</strong><span>Extensive high-voltage transmission network</span><em>Electricity grid</em></p>
            </div>
            <h3 class="export__special-title">SPECIAL TERMS</h3>
            <ul class="export__special">
              <li><strong>$0.05 kWh</strong> Competitive electricity rate</li>
              <li><strong>$0.08-$0.12</strong> Low-cost water supply</li>
            </ul>
          </div>
        </div>

        <div class="export__grid export__grid--bottom">
          <div class="export__box">
            <h3>SOFTLANDING SUPPORT</h3>
            <ul class="export__list">
              <li v-for="s in softlanding" :key="s">{{ s }}</li>
            </ul>
          </div>
          <div class="export__box">
            <h3>IT-VISA <span class="export__powered">powered by IT Park</span></h3>
            <ul class="export__list">
              <li v-for="v in itVisa" :key="v">{{ v }}</li>
            </ul>
          </div>
          <div class="export__box export__box--datavolt">
            <p class="export__datavolt-lead">Turn your Data Center into the cutting edge infrastructure for AI &amp; MINING</p>
            <div class="export__datavolt-stats">
              <span><strong>DATAVOLT</strong> capacity 500+ MW</span>
              <span><strong>$6.5B</strong> investment</span>
            </div>
            <p class="export__datavolt-invest"><strong>$100M+</strong> Investment in AI infrastructure</p>
            <p class="export__no-tax">NO CUSTOMS &amp; VAT — imported servers/GPUs exempt from taxes</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.export__panel {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  background: var(--panel);
}
.export__head {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 22px;
}
.export__bar {
  width: 4px;
  height: 22px;
  background: linear-gradient(180deg, var(--accent-2), var(--accent));
  border-radius: 2px;
}
.export__head h2 {
  font-size: 17px;
  margin: 0;
}

.export__grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1.3fr;
  gap: 16px;
  margin-bottom: 16px;
}
.export__grid--bottom {
  grid-template-columns: repeat(3, 1fr);
}

.export__box {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
}
.export__box h3 {
  font-size: 13px;
  margin: 0 0 14px;
  color: var(--accent-2);
  letter-spacing: 0.02em;
}

.export__benefits {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.export__benefits li {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 12px;
  color: var(--text-dim);
}
.export__benefits strong {
  min-width: 34px;
  color: var(--accent-2);
  font-size: 14px;
}

.export__reimburse p {
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 14px;
  font-size: 13px;
  color: var(--text-dim);
  margin: 0 0 10px;
}

.export__box--energy {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.export__energy-map {
  height: 60px;
  border-radius: var(--radius-sm);
  background: linear-gradient(160deg, #12241c, #0c1712);
  border: 1px solid var(--border);
}
.export__energy-stats p {
  margin: 0 0 8px;
  font-size: 12px;
  color: var(--text-dim);
  display: flex;
  flex-direction: column;
}
.export__energy-stats strong {
  color: var(--accent-2);
  font-size: 16px;
}
.export__energy-stats em {
  font-style: normal;
  font-size: 10px;
  color: var(--text-faint);
}
.export__special-title {
  margin: 4px 0 8px;
  font-size: 12px;
}
.export__special {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 6px;
  font-size: 12px;
  color: var(--text-dim);
}
.export__special strong {
  color: var(--accent-2);
  margin-right: 6px;
}

.export__list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
  font-size: 13px;
  color: var(--text-dim);
}
.export__powered {
  font-size: 10px;
  color: var(--text-faint);
  font-weight: 400;
  margin-left: 8px;
}

.export__box--datavolt {
  background: linear-gradient(160deg, rgba(62, 224, 138, 0.1), rgba(255, 255, 255, 0.02));
}
.export__datavolt-lead {
  font-size: 13px;
  color: var(--text);
  margin: 0 0 12px;
  font-weight: 600;
}
.export__datavolt-stats {
  display: flex;
  flex-direction: column;
  gap: 6px;
  font-size: 12px;
  color: var(--text-dim);
  margin-bottom: 10px;
}
.export__datavolt-invest {
  font-size: 13px;
  color: var(--accent-2);
  margin: 0 0 10px;
}
.export__no-tax {
  font-size: 11px;
  color: var(--text-faint);
  margin: 0;
}

@media (max-width: 1024px) {
  .export__grid,
  .export__grid--bottom {
    grid-template-columns: 1fr 1fr;
  }
}
@media (max-width: 640px) {
  .export__panel {
    padding: 18px;
  }
  .export__grid,
  .export__grid--bottom {
    grid-template-columns: 1fr;
  }
}
</style>
