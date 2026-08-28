<script setup>
import { ref, computed } from 'vue'

// Shared header logos
import Group848 from '../assets/images/Group-848.webp'
import Group849 from '../assets/images/Group-849.webp'

// Slide 1 — Digital Startups Program
import startupBaseIcon from '../assets/images/startupBase.webp'
import QRcode from '../assets/images/QRcode.webp'
import metric from '../assets/images/metric-container.webp'

// Slide 2 — Key Indicators of IT Park Members
import exportGeography from '../assets/images/exportGeography.webp'
import typeOfExport from '../assets/images/typeOfExport.webp'
import Revenue from '../assets/images/Revenue.webp'
import numberCompanies from '../assets/images/numberCompanies.webp'
import ForeignCapital from '../assets/images/ForeignCapital.webp'
import RevenueMembers from '../assets/images/RevenueMembers.webp'

// Slide 3 — Enterprise Uzbekistan
import Sandbox from '../assets/images/Sandbox.webp'
import exchange from '../assets/images/currency-exchange.webp'
import taxRefund from '../assets/images/tax-refund.webp'
import fileFolder from '../assets/images/file-folder.webp'
import databaseConnection from '../assets/images/database-connection.webp'
import Government from '../assets/images/services.webp'
import digitalBrain from '../assets/images/digital-brain.webp'
import earningsReport from '../assets/images/earnings-report.webp'
import globalNetwork from '../assets/images/global-network.webp'

// Slide 4 — Digital Service and Products Export Development
import FreeOfficeIcon from '../assets/images/FreeOffice.webp'
import Technical from '../assets/images/Technical.webp'
import farmImage from '../assets/images/farmImage.webp'
import RegistrationIcon from '../assets/images/Registration.webp'
import Banking from '../assets/images/Banking.webp'
import Turnkey from '../assets/images/Turnkey.webp'
import Talent from '../assets/images/Talent.webp'
import ITVISALOGO from '../assets/images/it-visa.webp'
import noWork from '../assets/images/noWork.webp'
import salary from '../assets/images/salary.webp'
import Dividends from '../assets/images/Dividends.webp'
import datavoltlogo from '../assets/images/datavoltlogo.webp'
import us from '../assets/images/us.webp'
import ger from '../assets/images/ger.webp'
import sa from '../assets/images/sa.webp'
import ci from '../assets/images/ci.webp'
import kr from '../assets/images/sk.webp'
import jp from '../assets/images/jp.webp'

/* -------------------------------------------------------------------- */
/*  Slide 1 data — Digital Startups Program                             */
/* -------------------------------------------------------------------- */
const startupItems = [
  { value: '100%', label: 'Reimbursement for patenting and trademark registration' },
  { value: '', icon: 'shield', label: 'Special legal regime "Regulatory Sandbox" for rapid piloting' },
  { value: '$50K', label: 'Reimbursement for mentor/trainer costs in acceleration programs' },
  { value: '1+1', label: 'Co-funding mechanism matching foreign investment dollar-for-dollar' },
  { value: '$20K', label: 'Reimbursement of international acceleration program costs' },
  { value: '1 YEAR', label: 'Free access to the massive Digital Data Platform for Startups' },
  { value: '1 YEAR', label: 'Free dedicated legal and financial consultations with top experts' },
  { value: '$10K', label: 'Awarding grants directly to winners of national hackathons and ideathons' }
]

/* -------------------------------------------------------------------- */
/*  Slide 2 data — Key Indicators of IT Park Members                    */
/* -------------------------------------------------------------------- */
const geography = [
  { label: 'NORTH AMERICA', value: '46%' },
  { label: 'CIS & APAC', value: '27%' },
  { label: 'EU AND UK', value: '21%' },
  { label: 'MENA', value: '6%' }
]
const offices = [
  { flag: us, name: 'USA' },
  { flag: ger, name: 'Germany' },
  { flag: sa, name: 'Saudi Arabia' },
  { flag: ci, name: 'China' },
  { flag: kr, name: 'South Korea' },
  { flag: jp, name: 'Japan' }
]
const bigStats = [
  { title: 'Number of Member Companies', value: '3 400+', growth: '22x', chart: numberCompanies },
  { title: 'Growth of Companies with Foreign Capital', value: '970+', growth: '127x', extra: 'Number of American capital companies', chart: ForeignCapital },
  { title: 'Revenue of Members (Million USD)', value: '2 800.0', growth: '127x', chart: RevenueMembers }
]

/* -------------------------------------------------------------------- */
/*  Slide 3 data — Enterprise Uzbekistan                                 */
/* -------------------------------------------------------------------- */
const features = [
  { title: 'Regulatory Sandbox', desc: 'Legally protected testing environment for new business models and frontier technologies.', icon: Sandbox },
  { title: 'Foreign exchange freedom', desc: 'Foreign currency operations, payroll, and capital flows without conversion mandates.', icon: exchange },
  { title: 'Tax & customs', desc: 'Corporate tax exemption for export-led companies; customs-duty exemption on equipment imports.', icon: taxRefund },
  { title: 'Labour relations', desc: 'International-grade employment structures aligned with global labour standards.', icon: fileFolder },
  { title: 'Personal data', desc: 'Internationally aligned data protection rules with full support for cross-border processing.', icon: databaseConnection },
  { title: 'Government services', desc: 'Full government services for foreign residents — including remote registration and licensing.', icon: Government },
  { title: 'Intellectual property', desc: 'Enhanced IP protections with specific provisions for AI-generated outputs and software assets.', icon: digitalBrain },
  { title: 'Investment attraction', desc: 'Investment instruments purpose-built for venture financing — SAFEs, convertibles, hybrid structures.', icon: earningsReport },
  { title: 'Export promotion', desc: 'Favourable operating conditions for export-driven companies with zero-friction outbound trade.', icon: globalNetwork }
]

// Each card shares the same gradient direction/structure — only the tint (bg color) changes per card
const featureGradients = [
  'linear-gradient(96.51deg, rgba(132, 255, 193, 0) -19.05%, rgba(132, 255, 193, 0.32) 100.49%)',
  'linear-gradient(94.25deg, rgba(255, 255, 255, 0.05) 0%, rgba(132, 235, 194, 0.22) 100.51%)',
  'linear-gradient(94.25deg, rgba(255, 255, 255, 0.05) 0%, rgba(132, 235, 194, 0.1) 100.51%)'
]
function featureBg(i) {
  return featureGradients[i % featureGradients.length]
}

/* -------------------------------------------------------------------- */
/*  Slide 4 data — Digital Service and Products Export Development       */
/* -------------------------------------------------------------------- */
const benefits = [
  { label: 'CORPORATE TAXES', value: '0%' },
  { label: 'SOCIAL TAX', value: '0%' },
  { label: 'PROPERTY & LAND TAX', value: '0%' },
  { label: 'VAT ON IMPORTED SERVICES', value: 'NO' },
  { label: 'TAX ON DIVIDENDS', value: '5%' },
  { label: 'PERSONAL INCOME TAX', value: '7.5%' }
]
const zeroRisk = [
  { icon: FreeOfficeIcon, text: 'Free office for 1 year' },
  { icon: Technical, text: 'Technical Equipment for 1 year' }
]
const energyStats = [
  { value: '9.3 GW', label: 'Major green, wind-powered energy capacity', tag: 'Wind farms' },
  { value: '1 885 km', label: 'Extensive high-voltage transmission network', tag: 'Electricity grid' }
]
const specialTerms = [
  { value: '$0.05 kWh', text: 'Competitive electricity rate' },
  { value: '$0.08-$0.12', text: 'Low-cost water supply' }
]
const softlanding = [
  { icon: RegistrationIcon, text: '3 days Company registration' },
  { icon: Banking, text: 'Banking support' },
  { icon: Turnkey, text: 'Turnkey Accounting and Legal Services' },
  { icon: Talent, text: 'Talent and Staff Recruitment' }
]
const itVisaList = [
  { icon: noWork, text: 'No work permit' },
  { icon: salary, text: 'Salary in foreign currency' },
  { icon: Dividends, text: 'Dividends in foreign currency' }
]
const extraCards = [
  { title: 'Fast-track construction', text: 'Accelerated Design-Procure-Build with streamlined land allocation in region' },
  { title: 'Direct international payments', text: 'Cross-border transactions without local bank intermediaries' }
]
/* -------------------------------------------------------------------- */
/*  Carousel logic                                                       */
/* -------------------------------------------------------------------- */
const slides = ['startups', 'indicators', 'enterprise', 'export']
const slideLabels = [
  'DIGITAL STARTUPS PROGRAM',
  'KEY INDICATORS OF IT PARK MEMBERS',
  'ENTERPRISE UZBEKISTAN',
  'DIGITAL SERVICE AND PRODUCTS EXPORT DEVELOPMENT'
]

const current = ref(0)
const direction = ref('slide-next')

function prev() {
  direction.value = 'slide-prev'
  current.value = (current.value - 1 + slides.length) % slides.length
}
function next() {
  direction.value = 'slide-next'
  current.value = (current.value + 1) % slides.length
}
function goTo(i) {
  direction.value = i > current.value ? 'slide-next' : 'slide-prev'
  current.value = i
}

const activeSlide = computed(() => slides[current.value])
</script>

<template>
  <section class="section showcase">
    <div class="container">
      <div class="showcase__panel">
        <!-- Shared header -->
        <div class="showcase__head">
          <div class="showcase__head-left">
            <span class="showcase__bar" aria-hidden="true"></span>
            <h2>{{ slideLabels[current] }}</h2>
          </div>
          <div class="showcase__logos">
            <img :src="Group848" alt="Ministry of Digital Technologies of the Republic of Uzbekistan" class="showcase__logo" />
            <img :src="Group849" alt="IT Park Uzbekistan" class="showcase__logo showcase__logo--itpark" />
          </div>
        </div>

        <!-- Slides -->
        <transition :name="direction" mode="out-in">
          <div :key="current" class="showcase__body">

            <!-- ============ SLIDE 1 — DIGITAL STARTUPS PROGRAM ============ -->
            <div v-if="activeSlide === 'startups'" class="startups">
              <div class="startups__grid">
                <div v-for="(item, i) in startupItems" :key="i" class="startups__item">
                  <span v-if="item.value" class="startups__value">{{ item.value }}</span>
                  <img v-else :src="metric" class="startups__value" alt="Startup Base" />
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
                <div class="startups__qr-box">
                  <div class="startups__qr-brand">
                    <img :src="startupBaseIcon" alt="Startup Base"
                    />
                  </div>
                  <img :src="QRcode" alt="QR code to Startup Base platform" class="startups__qr-code" />
                </div>
              </div>
            </div>

            <!-- ============ SLIDE 2 — KEY INDICATORS ============ -->
            <div v-else-if="activeSlide === 'indicators'" class="indicators">
              <div class="indicators__row indicators__row--top">
                <div class="indicators__box indicators__box--geo">
                  <img :src="exportGeography" alt="Export geography map" class="indicators__map" />
                </div>

                <div class="indicators__right">
                  <div class="indicators__box">
                    <img :src="typeOfExport" alt="Types of export breakdown" class="indicators__donut" />
                  </div>
                  <div class="indicators__box">
                    <img :src="Revenue" alt="ICT export revenue growth chart" class="indicators__chart" />
                  </div>
                  <div class="indicators__offices">
                    <h3>6 REPRESENTATIVE OFFICES ABROAD</h3>
                    <ul>
                      <li v-for="o in offices" :key="o.name">
                        <span class="indicators__flag">
                        <img :src="o.flag" alt="flag" width="32" height="32" />
                      </span>{{ o.name }}</li>
                    </ul>
                  </div>
                </div>
              </div>

              <div class="indicators__row indicators__row--bottom">
                <div v-for="s in bigStats" :key="s.title" class="indicators__box">
                  <img :src="s.chart" :alt="s.title" class="indicators__chart" />
                </div>
              </div>
            </div>

            <!-- ============ SLIDE 3 — ENTERPRISE UZBEKISTAN ============ -->
            <div v-else-if="activeSlide === 'enterprise'" class="features">
              <div class="features__grid">
                <article v-for="(f, i) in features" :key="f.title" class="features__card" :style="{ background: featureBg(i) }">
                  <div class="features__card-top">
                    <h3>{{ f.title }}</h3>
                    <span class="features__icon"><img :src="f.icon" :alt="f.title" /></span>
                  </div>
                  <p>{{ f.desc }}</p>
                </article>
              </div>
            </div>
            <div v-else class="export">
              <!-- Top row: Benefits | Zero Risk | Energy -->
              <div class="export__grid export__grid--top">
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
                    <p v-for="z in zeroRisk" :key="z.text">
                      <img :src="z.icon" :alt="z.text" />
                      <span>{{ z.text }}</span>
                    </p>
                  </div>
                </div>

                <div class="export__box export__box--energy">
                  <div class="export__energy-top">
                    <img :src="farmImage" alt="Map of Uzbekistan energy infrastructure" class="export__energy-map" />

                    <div class="export__energy-stats">
                      <div class="export__energy-stat">
                        <div class="export__energy-stat-main">
                          <strong>9.3 GW</strong>
                          <span class="export__energy-tag">Wind farms</span>
                        </div>
                        <p>Major green, wind-powered energy capacity</p>
                      </div>

                      <div class="export__energy-stat">
                        <div class="export__energy-stat-main">
                          <strong>1 885 km</strong>
                          <span class="export__energy-tag">Electricity grid</span>
                        </div>
                        <p>Extensive high-voltage transmission network</p>
                      </div>
                    </div>
                  </div>

                  <h3 class="export__special-title">SPECIAL TERMS</h3>

                  <div class="export__special">
                    <div class="export__special-item">
                      <span class="export__special-dot"></span>
                      <div>
                        <strong>$0.05 kWh</strong>
                        <span>Competitive electricity rate</span>
                      </div>
                    </div>
                    <div class="export__special-item">
                      <span class="export__special-dot"></span>
                      <div>
                        <strong>$0.08-$0.12</strong>
                        <span>Low-cost water supply</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Middle row: Fast-track | Direct payments -->
              <div class="export__grid export__grid--extra">
                <div v-for="c in extraCards" :key="c.title" class="export__box export__box--extra">
                  <h3>{{ c.title }}</h3>
                  <p>{{ c.text }}</p>
                </div>
              </div>

              <!-- Bottom row: Softlanding | IT-VISA | DataVolt -->
              <div class="export__grid export__grid--bottom">
                <div class="export__box">
                  <h3>SOFTLANDING SUPPORT</h3>
                  <ul class="export__list">
                    <li v-for="s in softlanding" :key="s.text">
                      <img :src="s.icon" :alt="s.text" />
                      <span>{{ s.text }}</span>
                    </li>
                  </ul>
                </div>

                <div class="export__box">
                  <h3 class="export__itvisa-title">
                    <img :src="ITVISALOGO" alt="IT-Visa" class="export__itvisa-logo" />
                    IT-VISA
                    <span class="export__powered">powered by IT Park</span>
                  </h3>
                  <ul class="export__list">
                    <li v-for="v in itVisaList" :key="v.text">
                      <img :src="v.icon" :alt="v.text" />
                      <span>{{ v.text }}</span>
                    </li>
                  </ul>
                </div>

                <div class="export__box export__box--datavolt">
                  <p class="export__datavolt-lead">
                    Turn your Data Center into the cutting edge infrastructure for AI &amp; MINING
                  </p>
                  <div class="export__datavolt-stats">
        <span>
          <img :src="datavoltlogo" alt="Datavolt" class="export__datavolt-logo" />
          capacity 500+ MW
        </span>
                    <span><strong>$6.5B</strong> investment</span>
                  </div>
                  <p class="export__datavolt-invest">
                    <strong>$100M+</strong> Investment in AI infrastructure
                  </p>
                  <p class="export__no-tax">
                    NO CUSTOMS &amp; VAT — imported servers/GPUs exempt from taxes
                  </p>
                </div>
              </div>
            </div>

          </div>
        </transition>

        <!-- Shared navigation -->
        <div class="showcase__nav">
          <button type="button" aria-label="Previous" @click="prev">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M15 5l-7 7 7 7" stroke="currentColor" stroke-width="2" stroke-linecap="round" /></svg>
          </button>
          <div class="showcase__dots">
            <span
                v-for="(s, i) in slides"
                :key="s"
                class="showcase__dot"
                :class="{ 'showcase__dot--active': i === current }"
                @click="goTo(i)"
            ></span>
          </div>
          <button type="button" class="showcase__nav-next" aria-label="Next" @click="next">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M9 5l7 7-7 7" stroke="#062015" stroke-width="2" stroke-linecap="round" /></svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* ===================================================================== */
/*  Shared panel / header / nav                                          */
/* ===================================================================== */
.showcase__panel {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  background: radial-gradient(70.61% 100% at 49.18% 100%, #0C1E5B 0%, #010101 100%);
  overflow: hidden;
}
.showcase__head {
  background: linear-gradient(90deg, #84FFC1 44.12%, rgba(132, 255, 193, 0) 100%);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  color: #121B26;
  padding: 13px 24px;
  border-top-right-radius: var(--radius-lg);
  border-top-left-radius: var(--radius-lg);
}
.showcase__head-left {
  display: flex;
  align-items: center;
  gap: 12px;
  min-width: 0;
}
.showcase__bar {
  width: 1px;
  height: 20px;
  flex-shrink: 0;
  background: rgba(18, 27, 38, 0.35);
  border-radius: 2px;
}
.showcase__head h2 {
  font-size: 17px;
  font-weight: 700;
  margin: 0;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.showcase__logos {
  display: flex;
  align-items: center;
  gap: 14px;
  flex-shrink: 0;
}
.showcase__logo {
  height: 32px;
  width: auto;
  object-fit: contain;
}

.showcase__body {
  padding: 24px 24px 0;
  min-height: 320px;
}

/* Slide transition */
.slide-next-enter-active,
.slide-next-leave-active,
.slide-prev-enter-active,
.slide-prev-leave-active {
  transition: opacity 0.28s ease, transform 0.32s ease;
}
.slide-next-enter-from { opacity: 0; transform: translateX(24px); }
.slide-next-leave-to { opacity: 0; transform: translateX(-24px); }
.slide-prev-enter-from { opacity: 0; transform: translateX(-24px); }
.slide-prev-leave-to { opacity: 0; transform: translateX(24px); }

.showcase__nav {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  padding: 24px;
}
.showcase__dots {
  display: flex;
  align-items: center;
  gap: 8px;
}
.showcase__dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}
.showcase__dot--active {
  background: var(--accent);
  transform: scale(1.3);
}
.showcase__nav button {
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
  flex-shrink: 0;
  transition: opacity 0.2s ease, transform 0.15s ease;
}
.showcase__nav button:hover { opacity: 0.8; transform: scale(1.05); }
.showcase__nav-next {
  background: var(--accent) !important;
  border-color: var(--accent) !important;
}

/* ===================================================================== */
/*  Slide 1 — Digital Startups Program                                   */
/* ===================================================================== */
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
  background: #FFFFFF0D;
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 14px 16px;
}
.startups__value {
  font-family: 'Manrope', sans-serif;
  text-align: center;
  font-size: 32px;
  font-weight: 800;
  color: var(--accent-2);
  min-width: 100px;
}
.startups__icon {
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 64px;
}
.startups__item p {
  font-family: 'Manrope', sans-serif;
  margin: 0;
  font-size: 16px;
  color: #ffffff;
  line-height: 1.4;
}

.startups__footer {
  display: flex;
  align-items: center;
  gap: 20px;
  border-radius: var(--radius-md);
  margin-bottom: 24px;
}
.startups__footer p {
  background: linear-gradient(94.25deg, rgba(132, 255, 193, 0) 0%, rgba(132, 255, 193, 0.4) 100.51%);
  padding: 18px 22px;
  border-radius: var(--radius-md);
  margin: 0;
  font-size: 18px;
  font-weight: 700;
  color: var(--text);
  line-height: 1.5;
  flex: 1;
}
.startups__qr-box {
  display: flex;
  align-items: center;
  gap: 14px;
  flex-shrink: 0;
  background: rgba(0, 0, 0, 0.18);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 16px;
}
.startups__qr-brand {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  font-weight: 700;
  color: var(--text);
  white-space: nowrap;
}
.startups__qr-brand img { width: 155px; height: 36px; }
.startups__qr-code { width: 88px; height: 88px; border-radius: 6px; flex-shrink: 0; }

/* ===================================================================== */
/*  Slide 2 — Key Indicators                                             */
/* ===================================================================== */
.indicators__row {
  display: grid;
  grid-template-columns: 1fr 1.4fr ;
  gap: 16px;
  margin-bottom: 16px;
}
.indicators__right {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.indicators__right > :nth-child(3) {
  grid-column: span 2;
}

.indicators__row--bottom {
  grid-template-columns: repeat(3, 1fr);
}
.indicators__box {
  background: #FFFFFF0D;
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
}
.indicators__box h3 {
  font-size: 14px;
  margin: 0 0 12px;
  color: var(--text-dim);
}
.indicators__box h3 small { color: var(--text-faint); font-weight: 400; }

.indicators__map { width: 100%; height: auto; margin-bottom: 10px; }
.indicators__box--geo ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.indicators__box--geo li strong { display: block; color: var(--accent-2); font-size: 18px; }
.indicators__box--geo li span { font-size: 11px; color: var(--text-faint); }

.indicators__donut { display: block; width: 100%; height: 100%; }
.indicators__chart { display: block; width: 100%; height: 100%; }

.indicators__growth { margin: 0 0 10px; font-size: 13px; color: var(--text-dim); }
.indicators__growth strong { color: var(--accent-2); font-size: 20px; margin-right: 4px; }
.indicators__extra { font-size: 11px; color: var(--accent-2); margin: -6px 0 10px; }

.indicators__offices {
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 16px 18px;
  margin-bottom: 16px;
  background: #FFFFFF0D;
}
.indicators__offices h3 { font-size: 13px; margin: 0 0 12px; color: var(--text-dim); text-align: center; }
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
.indicators__offices li { display: flex; align-items: center; gap: 6px; }
.indicators__flag { font-size: 16px; line-height: 1; }

/* ===================================================================== */
/*  Slide 3 — Enterprise Uzbekistan                                      */
/* ===================================================================== */
.features__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 24px;
}
.features__card {
  background: #FFFFFF0D;
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 20px;
}
.features__card-top {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 10px;
}
.features__card h3 { font-size: 17px; margin: 0; color: var(--text); }
.features__icon {
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  border-radius: 10px;
  background: rgba(62, 224, 138, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
}
.features__icon img { width: 20px; height: 20px; }
.features__card p { font-size: 13px; color: var(--text-dim); line-height: 1.5; margin: 0; }

/* ===================================================================== */
/*  Slide 4 — Digital Service and Products Export Development             */
/* ===================================================================== */
.export__grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1.3fr;
  gap: 16px;
  margin-bottom: 16px;
}
.export__grid--extra {
  grid-template-columns: repeat(2, 1fr);
}
.export__grid--bottom {
  grid-template-columns: repeat(3, 1fr);
  margin-bottom: 24px;
}
.export__box {
  background: #FFFFFF0D;
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
}
.export__box h3 {
  font-size: 13px;
  margin: 0 0 14px;
  color: var(--accent-2);
  letter-spacing: 0.02em;
  display: flex;
  align-items: center;
  gap: 8px;
}

.export__benefits { list-style: none; margin: 0; padding: 0; display: flex; flex-direction: column; gap: 10px; }
.export__benefits li { display: flex; align-items: center; gap: 12px; font-size: 12px; color: var(--text-dim); }
.export__benefits strong { min-width: 34px; color: var(--accent-2); font-size: 14px; }

.export__reimburse p {
  display: flex;
  align-items: center;
  gap: 12px;
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 14px;
  font-size: 13px;
  color: var(--text-dim);
  margin: 0 0 10px;
}
.export__reimburse p:last-child { margin-bottom: 0; }
.export__reimburse img { width: 22px; height: 22px; flex-shrink: 0; }

.export__box--energy { display: flex; flex-direction: column; gap: 12px; }
.export__energy-map {
  width: 100%;
  height: 60px;
  object-fit: contain;
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
  align-items: flex-start;
  gap: 2px;
  position: relative;
}
.export__energy-stats strong { color: var(--accent-2); font-size: 16px; }
.export__energy-tag {
  align-self: flex-end;
  margin-top: -18px;
  font-size: 10px;
  color: var(--accent-2);
  background: rgba(62, 224, 138, 0.12);
  border-radius: 20px;
  padding: 3px 10px;
}
.export__special-title { margin: 4px 0 8px; font-size: 12px; }
.export__special { list-style: none; margin: 0; padding: 0; display: flex; flex-direction: column; gap: 6px; font-size: 12px; color: var(--text-dim); }
.export__special strong { color: var(--accent-2); margin-right: 6px; }

.export__box--extra p { margin: 0; font-size: 12px; color: var(--text-dim); line-height: 1.5; }

.export__list { list-style: none; margin: 0; padding: 0; display: flex; flex-direction: column; gap: 10px; font-size: 13px; color: var(--text-dim); }
.export__list li { display: flex; align-items: center; gap: 10px; }
.export__list img { width: 20px; height: 20px; flex-shrink: 0; }
.export__powered { font-size: 10px; color: var(--text-faint); font-weight: 400; margin-left: 8px; }
.export__itvisa-logo { width: 18px; height: 18px; }

.export__box--datavolt { background: linear-gradient(160deg, rgba(62, 224, 138, 0.14), #FFFFFF0D); }
.export__datavolt-lead { font-size: 13px; color: var(--text); margin: 0 0 12px; font-weight: 600; }
.export__datavolt-stats { display: flex; flex-direction: column; gap: 6px; font-size: 12px; color: var(--text-dim); margin-bottom: 10px; }
.export__datavolt-stats span { display: flex; align-items: center; gap: 6px; }
.export__datavolt-logo { height: 14px; width: auto; }
.export__datavolt-invest { font-size: 13px; color: var(--accent-2); margin: 0 0 10px; }
.export__no-tax { font-size: 11px; color: var(--text-faint); margin: 0; }

/* ===================================================================== */
/*  Responsive                                                           */
/* ===================================================================== */
@media (max-width: 1024px) {
  .indicators__row,
  .indicators__row--bottom,
  .export__grid,
  .export__grid--bottom {
    grid-template-columns: 1fr 1fr;
  }
  .features__grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 640px) {
  .showcase__head { flex-wrap: wrap; padding: 12px 16px; }
  .showcase__body { padding: 16px 16px 0; }
  .showcase__nav { padding: 16px; }
  .startups__grid { grid-template-columns: 1fr; }
  .startups__footer { flex-direction: column; align-items: stretch; }
  .startups__qr-box { justify-content: space-between; }
  .indicators__row,
  .indicators__row--bottom,
  .export__grid,
  .export__grid--extra,
  .export__grid--bottom {
    grid-template-columns: 1fr;
  }
  .indicators__box--geo ul { grid-template-columns: 1fr 1fr; }
  .features__grid { grid-template-columns: 1fr; }
}
/* ===== Energy box — Figma match ===== */
.export__box--energy {
  display: flex;
  flex-direction: column;
  gap: 14px;
  padding: 16px 18px;
}

.export__energy-top {
  display: flex;
  align-items: center;
  gap: 16px;
}

.export__energy-map {
  width: 110px;
  height: 90px;
  object-fit: contain;
  flex-shrink: 0;
  border-radius: 8px;
}

.export__energy-stats {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.export__energy-stat-main {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  margin-bottom: 2px;
}

.export__energy-stat strong {
  font-size: 18px;
  font-weight: 700;
  color: var(--accent-2);
  line-height: 1.2;
  white-space: nowrap;
}

.export__energy-tag {
  font-size: 11px;
  font-weight: 500;
  color: var(--accent-2);
  background: rgba(62, 224, 138, 0.15);
  border: 1px solid rgba(62, 224, 138, 0.25);
  border-radius: 20px;
  padding: 3px 10px;
  white-space: nowrap;
}

.export__energy-stat p {
  margin: 0;
  font-size: 12px;
  color: var(--text-dim);
  line-height: 1.35;
}

/* SPECIAL TERMS */
.export__special-title {
  font-size: 13px !important;
  font-weight: 700;
  color: var(--accent-2);
  margin: 2px 0 0 !important;
  letter-spacing: 0.03em;
  text-align: center;
}

.export__special {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

.export__special-item {
  display: flex;
  align-items: flex-start;
  gap: 8px;
  background: rgba(62, 224, 138, 0.08);
  border: 1px solid rgba(62, 224, 138, 0.2);
  border-radius: 12px;
  padding: 10px 12px;
}

.export__special-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--accent-2);
  margin-top: 6px;
  flex-shrink: 0;
}

.export__special-item strong {
  display: block;
  font-size: 13px;
  font-weight: 700;
  color: var(--accent-2);
  line-height: 1.25;
}

.export__special-item span {
  display: block;
  font-size: 11px;
  color: var(--text-dim);
  line-height: 1.3;
  margin-top: 2px;
}
</style>