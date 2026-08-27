<script setup>
import { reactive, ref } from 'vue'

const countries = ['Uzbekistan', 'Kazakhstan', 'United States', 'United Kingdom', 'Germany', 'Japan', 'South Korea', 'Other']
const attendingAs = ['Investor', 'Founder / Startup', 'Corporate delegate', 'Government official', 'Media / Press']
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
  'AI Native: Ideas to Innovation'
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
const tracksOpen = ref(false)
const submitted = ref(false)

function toggleTrack(track) {
  const idx = form.selectedTracks.indexOf(track)
  if (idx === -1) {
    form.selectedTracks.push(track)
  } else {
    form.selectedTracks.splice(idx, 1)
  }
}

function validate() {
  Object.keys(errors).forEach((k) => delete errors[k])
  if (!form.fullName.trim()) errors.fullName = 'Full name is required'
  if (!/^\S+@\S+\.\S+$/.test(form.email)) errors.email = 'Enter a valid email address'
  if (!form.country) errors.country = 'Select your country'
  if (!form.attendingAs) errors.attendingAs = 'Select how you are attending'
  if (!form.consent) errors.consent = 'Please confirm consent to continue'
  return Object.keys(errors).length === 0
}

function onSubmit() {
  if (validate()) {
    submitted.value = true
  }
}

function trackSummary() {
  if (!form.selectedTracks.length) return 'Select track(s)...'
  if (form.selectedTracks.length === 1) return form.selectedTracks[0]
  return `${form.selectedTracks.length} tracks selected`
}
</script>

<template>
  <section id="register" class="section register">
    <div class="container register__container">
      <div v-if="!submitted" class="register__card">
        <h2>Register for ICTWEEK Uzbekistan 2026</h2>
        <p class="register__sub">
          Join global tech leaders, enterprise delegates, and investors in Tashkent.
          Complete your details below to secure your pass.
        </p>

        <form novalidate @submit.prevent="onSubmit">
          <div class="register__grid">
            <div class="field">
              <label for="fullName">Full name</label>
              <input id="fullName" v-model="form.fullName" type="text" placeholder="e.g. John Doe" :aria-invalid="!!errors.fullName" />
              <span v-if="errors.fullName" class="field__error">{{ errors.fullName }}</span>
            </div>

            <div class="field">
              <label for="country">Country</label>
              <select id="country" v-model="form.country" :aria-invalid="!!errors.country">
                <option value="" disabled>Select country...</option>
                <option v-for="c in countries" :key="c" :value="c">{{ c }}</option>
              </select>
              <span v-if="errors.country" class="field__error">{{ errors.country }}</span>
            </div>

            <div class="field">
              <label for="email">Email</label>
              <input id="email" v-model="form.email" type="email" placeholder="e.g. alex@company.com" :aria-invalid="!!errors.email" />
              <span v-if="errors.email" class="field__error">{{ errors.email }}</span>
            </div>

            <div class="field">
              <label for="phone">Phone number</label>
              <input id="phone" v-model="form.phone" type="tel" placeholder="e.g. +1 (555) 019-2834" />
            </div>

            <div class="field">
              <label for="company">Company</label>
              <input id="company" v-model="form.company" type="text" placeholder="e.g. Tech Global Inc." />
            </div>

            <div class="field">
              <label for="position">Position</label>
              <input id="position" v-model="form.position" type="text" placeholder="e.g. Managing Director" />
            </div>

            <div class="field">
              <label for="attendingAs">I am attending as</label>
              <select id="attendingAs" v-model="form.attendingAs" :aria-invalid="!!errors.attendingAs">
                <option value="" disabled>Select category...</option>
                <option v-for="a in attendingAs" :key="a" :value="a">{{ a }}</option>
              </select>
              <span v-if="errors.attendingAs" class="field__error">{{ errors.attendingAs }}</span>
            </div>

            <div class="field field--dropdown">
              <label id="tracksLabel">Event track(s) you plan to attend (Select all that apply)</label>
              <button
                type="button"
                class="field__dropdown-btn"
                aria-haspopup="listbox"
                :aria-expanded="tracksOpen"
                aria-labelledby="tracksLabel"
                @click="tracksOpen = !tracksOpen"
              >
                {{ trackSummary() }}
                <svg width="10" height="6" viewBox="0 0 10 6" fill="none" aria-hidden="true">
                  <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
                </svg>
              </button>
              <ul v-if="tracksOpen" class="field__dropdown-list" role="listbox" aria-multiselectable="true">
                <li v-for="t in tracks" :key="t">
                  <label>
                    <input type="checkbox" :checked="form.selectedTracks.includes(t)" @change="toggleTrack(t)" />
                    {{ t }}
                  </label>
                </li>
              </ul>
            </div>

            <div class="field">
              <label for="source">How did you hear about us?</label>
              <select id="source" v-model="form.source">
                <option value="" disabled>Select source...</option>
                <option v-for="s in sources" :key="s" :value="s">{{ s }}</option>
              </select>
            </div>

            <div class="field">
              <label for="focalPoint">Name of focal point in IT Park (if available)</label>
              <input id="focalPoint" v-model="form.focalPoint" type="text" placeholder="e.g. Contact person or team member name" />
            </div>
          </div>

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
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" aria-hidden="true">
              <path d="M2 10L10 2M10 2H4M10 2v6" stroke="#062015" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </button>
        </form>
      </div>

      <div v-else class="register__thanks">
        <div class="register__thanks-icon" aria-hidden="true">
          <svg width="30" height="30" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="8" r="4" stroke="var(--accent)" stroke-width="1.6" />
            <path d="M4 20c0-3.3 3.6-6 8-6s8 2.7 8 6" stroke="var(--accent)" stroke-width="1.6" />
            <path d="M9 12l2 2 4-4" stroke="var(--accent)" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" />
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
  background: var(--panel);
}
.register__card h2,
.register__thanks h2 {
  font-size: 28px;
  text-align: center;
  margin: 0 0 10px;
}
.register__sub {
  text-align: center;
  color: var(--text-dim);
  font-size: 14px;
  margin: 0 0 30px;
}

.register__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px 24px;
  margin-bottom: 20px;
}
.field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.field label {
  font-size: 12.5px;
  color: var(--text-dim);
}
.field input,
.field select {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 14px;
  color: var(--text);
  font-size: 14px;
  width: 100%;
  appearance: none;
}
.field select {
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6' viewBox='0 0 10 6'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%23a9b6b0' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 14px center;
  padding-right: 30px;
}
.field input::placeholder {
  color: var(--text-faint);
}
.field input:focus,
.field select:focus {
  outline: none;
  border-color: var(--accent);
}
.field input[aria-invalid='true'],
.field select[aria-invalid='true'] {
  border-color: #e0693e;
}
.field__error {
  font-size: 11.5px;
  color: #ff9270;
}

.field--dropdown {
  position: relative;
}
.field__dropdown-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 14px;
  color: var(--text-faint);
  font-size: 14px;
  cursor: pointer;
  text-align: left;
}
.field__dropdown-list {
  position: absolute;
  top: calc(100% + 6px);
  left: 0;
  right: 0;
  z-index: 5;
  background: var(--panel-2);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  list-style: none;
  margin: 0;
  padding: 6px;
  max-height: 220px;
  overflow-y: auto;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
}
.field__dropdown-list li label {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 8px;
  font-size: 13px;
  color: var(--text-dim);
  border-radius: 6px;
  cursor: pointer;
}
.field__dropdown-list li label:hover {
  background: rgba(255, 255, 255, 0.05);
}

.register__consent {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  font-size: 12.5px;
  color: var(--text-dim);
  line-height: 1.5;
  margin-bottom: 6px;
  cursor: pointer;
}
.register__consent input {
  margin-top: 3px;
}
.register__submit {
  display: flex;
  width: 100%;
  margin-top: 18px;
  padding: 14px;
  font-size: 15px;
}

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
    padding: 26px;
  }
  .register__grid {
    grid-template-columns: 1fr;
  }
}
</style>
