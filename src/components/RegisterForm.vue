<script setup>
import { reactive, ref, computed, onMounted, onUnmounted } from 'vue'

const countries = [
  'Uzbekistan', 'Kazakhstan', 'United States', 'United Kingdom',
  'Germany', 'Japan', 'South Korea', 'Other'
]

const attendingAsOptions = [
  'Investor',
  'Founder / Startup',
  'Corporate delegate',
  'Government official',
  'Media / Press'
]

const sources = [
  'Online Advertisement (Instagram, Facebook, LinkedIn, Google)',
  'Partner Network',
  'IT Park Representative',
  'Organic Search / Website'
]

const tracks = [
  'Enterprise Uzbekistan Summit',
  'Startup & Venture Summit',
  'Startup Blink Awards',
  'Startup World Cup - Uzbekistan Regional Final',
  'Tech & Service Outsourcing Conference',
  'Global Bridge (International Partnerships)',
  'GameGap: GameDev Conference',
  'AI Native: Ideas to Innovation',
  'Ignyte Challenge',
  'Taqdimot (Startup pitches)'
]

const form = reactive({
  fullName: '',
  country: '',
  email: '',
  phone: '',
  company: '',
  position: '',
  attendingAs: '',
  source: '',
  focalPoint: '',
  consent: false,
  selectedTracks: []
})

const errors = reactive({})
const openDropdown = ref(null) // 'country' | 'attendingAs' | 'tracks' | 'source' | null
const submitted = ref(false)

const trackSummary = computed(() => {
  const len = form.selectedTracks.length
  if (len === 0) return 'Select track(s)...'
  if (len === 1) return form.selectedTracks[0]
  return `${len} tracks selected`
})

function toggleDropdown(name) {
  openDropdown.value = openDropdown.value === name ? null : name
}

function selectOption(field, value) {
  form[field] = value
  openDropdown.value = null
}

function toggleTrack(track) {
  const idx = form.selectedTracks.indexOf(track)
  if (idx === -1) form.selectedTracks.push(track)
  else form.selectedTracks.splice(idx, 1)
}

function validate() {
  Object.keys(errors).forEach(k => delete errors[k])

  if (!form.fullName.trim()) errors.fullName = 'Full name is required'
  if (!/^\S+@\S+\.\S+$/.test(form.email)) errors.email = 'Enter a valid email address'
  if (!form.country) errors.country = 'Select your country'
  if (!form.attendingAs) errors.attendingAs = 'Select how you are attending'
  if (!form.consent) errors.consent = 'Please confirm consent to continue'

  return Object.keys(errors).length === 0
}

function onSubmit() {
  if (validate()) submitted.value = true
}

function handleClickOutside(e) {
  if (!e.target.closest('.field--dropdown')) {
    openDropdown.value = null
  }
}

onMounted(() => document.addEventListener('click', handleClickOutside))
onUnmounted(() => document.removeEventListener('click', handleClickOutside))
</script>

<template>
  <section id="register" class="section register">
    <div class="container register__container">
      <div v-if="!submitted" class="register__card">
        <h2>Register for ICTWEEK Uzbekistan 2026</h2>
        <p class="register__sub">
          Join global tech leaders, enterprise delegates, and investors in Tashkent.<br>
          Complete your details below to secure your pass.
        </p>

        <form novalidate @submit.prevent="onSubmit">
          <div class="register__grid">
            <!-- Full name -->
            <div class="field">
              <label for="fullName">Full name</label>
              <input
                  id="fullName"
                  v-model="form.fullName"
                  type="text"
                  placeholder="e.g. John Doe"
                  :aria-invalid="!!errors.fullName"
              />
              <span v-if="errors.fullName" class="field__error">{{ errors.fullName }}</span>
            </div>

            <!-- Country (custom) -->
            <div class="field field--dropdown">
              <label>Country</label>
              <button
                  type="button"
                  class="field__dropdown-btn"
                  :class="{ 'is-open': openDropdown === 'country', 'has-value': form.country }"
                  @click.stop="toggleDropdown('country')"
              >
                <span>{{ form.country || 'Select country...' }}</span>
                <svg width="10" height="6" viewBox="0 0 10 6" fill="none">
                  <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
              </button>
              <ul v-show="openDropdown === 'country'" class="field__dropdown-list">
                <li v-for="c in countries" :key="c">
                  <button
                      type="button"
                      class="dropdown-item"
                      :class="{ active: form.country === c }"
                      @click="selectOption('country', c)"
                  >
                    {{ c }}
                  </button>
                </li>
              </ul>
              <span v-if="errors.country" class="field__error">{{ errors.country }}</span>
            </div>

            <!-- Email -->
            <div class="field">
              <label for="email">Email</label>
              <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  placeholder="e.g. alex@company.com"
                  :aria-invalid="!!errors.email"
              />
              <span v-if="errors.email" class="field__error">{{ errors.email }}</span>
            </div>

            <!-- Phone -->
            <div class="field">
              <label for="phone">Phone number</label>
              <input
                  id="phone"
                  v-model="form.phone"
                  type="tel"
                  placeholder="e.g. +1 (555) 019-2834"
              />
            </div>

            <!-- Company -->
            <div class="field">
              <label for="company">Company</label>
              <input
                  id="company"
                  v-model="form.company"
                  type="text"
                  placeholder="e.g. Tech Global Inc."
              />
            </div>

            <!-- Position -->
            <div class="field">
              <label for="position">Position</label>
              <input
                  id="position"
                  v-model="form.position"
                  type="text"
                  placeholder="e.g. Managing Director"
              />
            </div>

            <!-- I am attending as (custom) -->
            <div class="field field--dropdown">
              <label>I am attending as</label>
              <button
                  type="button"
                  class="field__dropdown-btn"
                  :class="{ 'is-open': openDropdown === 'attendingAs', 'has-value': form.attendingAs }"
                  @click.stop="toggleDropdown('attendingAs')"
              >
                <span>{{ form.attendingAs || 'Select category...' }}</span>
                <svg width="10" height="6" viewBox="0 0 10 6" fill="none">
                  <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
              </button>
              <ul v-show="openDropdown === 'attendingAs'" class="field__dropdown-list">
                <li v-for="a in attendingAsOptions" :key="a">
                  <button
                      type="button"
                      class="dropdown-item"
                      :class="{ active: form.attendingAs === a }"
                      @click="selectOption('attendingAs', a)"
                  >
                    {{ a }}
                  </button>
                </li>
              </ul>
              <span v-if="errors.attendingAs" class="field__error">{{ errors.attendingAs }}</span>
            </div>

            <!-- Event tracks (multi) -->
            <div class="field field--dropdown">
              <label>Event track(s) you plan to attend (Select all that apply)</label>
              <button
                  type="button"
                  class="field__dropdown-btn"
                  :class="{ 'is-open': openDropdown === 'tracks', 'has-value': form.selectedTracks.length }"
                  @click.stop="toggleDropdown('tracks')"
              >
                <span>{{ trackSummary }}</span>
                <svg width="10" height="6" viewBox="0 0 10 6" fill="none">
                  <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
              </button>
              <ul v-show="openDropdown === 'tracks'" class="field__dropdown-list">
                <li v-for="t in tracks" :key="t">
                  <label class="dropdown-item checkbox">
                    <input
                        type="checkbox"
                        :checked="form.selectedTracks.includes(t)"
                        @change="toggleTrack(t)"
                    />
                    <span>{{ t }}</span>
                  </label>
                </li>
              </ul>
            </div>

            <!-- How did you hear about us? -->
            <div class="field field--dropdown">
              <label>How did you hear about us?</label>
              <button
                  type="button"
                  class="field__dropdown-btn"
                  :class="{ 'is-open': openDropdown === 'source', 'has-value': form.source }"
                  @click.stop="toggleDropdown('source')"
              >
                <span>{{ form.source || 'Select source...' }}</span>
                <svg width="10" height="6" viewBox="0 0 10 6" fill="none">
                  <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
              </button>
              <ul v-show="openDropdown === 'source'" class="field__dropdown-list">
                <li v-for="s in sources" :key="s">
                  <label class="dropdown-item radio">
                    <input
                        type="radio"
                        name="source"
                        :value="s"
                        :checked="form.source === s"
                        @change="selectOption('source', s)"
                    />
                    <span>{{ s }}</span>
                  </label>
                </li>
              </ul>
            </div>

            <!-- Focal point -->
            <div class="field">
              <label for="focalPoint">Name of focal point in IT Park (if available)</label>
              <input
                  id="focalPoint"
                  v-model="form.focalPoint"
                  type="text"
                  placeholder="e.g. Contact person or team member name"
              />
            </div>
          </div>

          <!-- Consent -->
          <label class="register__consent">
            <input type="checkbox" v-model="form.consent" :aria-invalid="!!errors.consent" />
            <span>
              Yes, I agree that IT Park Uzbekistan team may contact me by e-mail to inquire
              about my request, and I am aware that my shared personal data will be saved.
              This consent can be withdrawn at any time.
            </span>
          </label>
          <span v-if="errors.consent" class="field__error">{{ errors.consent }}</span>

          <button type="submit" class="btn btn-primary register__submit">
            Register now
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
              <path d="M2 10L10 2M10 2H4M10 2v6" stroke="#062015" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </form>
      </div>

      <!-- Success -->
      <div v-else class="register__thanks">
        <div class="register__thanks-icon">
          <svg width="30" height="30" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="8" r="4" stroke="var(--accent)" stroke-width="1.6"/>
            <path d="M4 20c0-3.3 3.6-6 8-6s8 2.7 8 6" stroke="var(--accent)" stroke-width="1.6"/>
            <path d="M9 12l2 2 4-4" stroke="var(--accent)" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <h2>Registration Submitted — Welcome to ICTWEEK 2026!</h2>
        <p>
          Thank you for registering. A confirmation email is on its way, and a member of
          the IT Park Uzbekistan team will contact you shortly with your official delegate
          pass and next steps.
        </p>
        <a href="#top" class="btn btn-outline">Back to homepage</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.register__container {
  max-width: 900px;
}

.register__card,
.register__thanks {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 40px;
  background: #121B2666;
  backdrop-filter: blur(12px);
}

.register__card h2,
.register__thanks h2 {
  font-size: 28px;
  text-align: center;
  margin: 0 0 10px;
  font-weight: 600;
}

.register__sub {
  text-align: center;
  color: var(--text-dim);
  font-size: 14px;
  margin: 0 0 32px;
  line-height: 1.5;
}

.register__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px 24px;
  margin-bottom: 22px;
}

.field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.field label {
  font-size: 12.5px;
  color: var(--text-dim);
  font-weight: 500;
}

.field input {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 14px;
  color: var(--text);
  font-size: 14px;
  width: 100%;
  transition: border-color 0.15s ease;
}

.field input::placeholder {
  color: var(--text-faint);
}

.field input:focus {
  outline: none;
  border-color: var(--accent);
}

.field input[aria-invalid='true'] {
  border-color: #e0693e;
}

.field__error {
  font-size: 11.5px;
  color: #ff9270;
  margin-top: 2px;
}

/* ===== Custom Dropdowns ===== */
.field--dropdown {
  position: relative;
}

.field__dropdown-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 14px;
  color: var(--text-faint);
  font-size: 14px;
  cursor: pointer;
  text-align: left;
  transition: border-color 0.15s ease;
}

.field__dropdown-btn.has-value {
  color: var(--text);
}

.field__dropdown-btn.is-open {
  border-color: var(--accent);
}

.field__dropdown-btn svg {
  flex-shrink: 0;
  transition: transform 0.2s ease;
  color: var(--text-faint);
}

.field__dropdown-btn.is-open svg {
  transform: rotate(180deg);
}

.field__dropdown-list {
  position: absolute;
  top: calc(100% + 6px);
  left: 0;
  right: 0;
  z-index: 30;
  background: #1a2433;
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  list-style: none;
  margin: 0;
  padding: 6px;
  max-height: 260px;
  overflow-y: auto;
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.5);
}

/* Single select items */
.dropdown-item {
  display: block;
  width: 100%;
  padding: 10px 12px;
  font-size: 13.5px;
  color: var(--text-dim);
  background: transparent;
  border: none;
  border-radius: 6px;
  text-align: left;
  cursor: pointer;
  transition: background 0.12s ease, color 0.12s ease;
}

.dropdown-item:hover {
  background: rgba(255, 255, 255, 0.06);
  color: var(--text);
}

.dropdown-item.active {
  background: rgba(0, 200, 150, 0.15);
  color: var(--accent);
}

/* Checkbox & Radio items */
.dropdown-item.checkbox,
.dropdown-item.radio {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
}

.dropdown-item.checkbox input,
.dropdown-item.radio input {
  width: 16px;
  height: 16px;
  margin: 0;
  accent-color: var(--accent);
  cursor: pointer;
  flex-shrink: 0;
}

.dropdown-item.checkbox span,
.dropdown-item.radio span {
  line-height: 1.35;
}

/* Consent */
.register__consent {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  font-size: 12.5px;
  color: var(--text-dim);
  line-height: 1.55;
  margin-bottom: 8px;
  cursor: pointer;
}

.register__consent input {
  margin-top: 3px;
  width: 16px;
  height: 16px;
  accent-color: var(--accent);
  flex-shrink: 0;
}

.register__submit {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  margin-top: 20px;
  padding: 14px;
  font-size: 15px;
  font-weight: 600;
}

/* Success */
.register__thanks {
  text-align: center;
}

.register__thanks-icon {
  width: 60px;
  height: 60px;
  margin: 0 auto 18px;
  border-radius: 50%;
  background: var(--accent-soft);
  display: flex;
  align-items: center;
  justify-content: center;
}

.register__thanks p {
  color: var(--text-dim);
  font-size: 14px;
  line-height: 1.6;
  max-width: 480px;
  margin: 0 auto 24px;
}

@media (max-width: 768px) {
  .register__card,
  .register__thanks {
    padding: 26px 20px;
  }
  .register__grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  .register__card h2 {
    font-size: 22px;
  }
}
</style>