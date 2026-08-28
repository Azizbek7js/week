<script setup>
import { computed } from 'vue'

// Confident name-matches (file name clearly maps to the brand):
import Plug from '../assets/images/Plug.webp'
import Mit from '../assets/images/Mit.webp'
import Google from '../assets/images/Google.webp'
import Aws from '../assets/images/aws.webp'
import Dealroom from '../assets/images/Dealroom.webp'
import Domino from '../assets/images/domino.webp'
import Accesa from '../assets/images/Accesa.webp'
import Salesforce from '../assets/images/Salesforce.webp'
import ey from '../assets/images/ey.webp'
import GLOBAL from '../assets/images/GLOBAL.webp'
import gbtp from '../assets/images/gbtp.webp'
import polyavalent from '../assets/images/polyavalent.webp'

// Generic Figma export names — best-guess mapping, please verify these four:
import Group from '../assets/images/Group.webp' // guessed: web summit
import Startup from '../assets/images/Startup.webp' // guessed: StartupBlink
import Container from '../assets/images/Container.webp' // guessed: Startup Genome
import svgexport from '../assets/images/svgexport.webp' // guessed: Sturgeon Capital

// NOTE: no imported file for "Alchemist Accelerator", "Golden Gate Ventures",
// "SPS Commerce" — export these three from Figma and add them below to
// replace their text-fallback cards.
const logos = [
  { name: 'web summit', src: Group },
  { name: 'Plug and Play', src: Plug },
  { name: 'MIT', src: Mit },
  { name: 'Google for Startups', src: Google },
  { name: 'AWS', src: Aws },
  { name: 'Alchemist Accelerator', src: null },
  { name: 'dealroom.co', src: Dealroom },
  { name: 'StartupBlink', src: Startup },
  { name: 'DOMINO', src: Domino },
  { name: 'Startup Genome', src: Container },
  { name: 'accesa', src: Accesa },
  { name: 'Sturgeon Capital', src: svgexport },
  { name: 'salesforce.org', src: Salesforce },
  { name: 'EY', src: ey },
  { name: 'Global Startup Awards', src: GLOBAL },
  { name: 'GBTP', src: gbtp },
  { name: 'Polyvalent', src: polyavalent },
  { name: 'Golden Gate Ventures', src: null },
  { name: 'SPS Commerce', src: null }
]

// Split into rows of 5, so the final (partial) row can be laid out on its
// own grid and stretch to fill the full width instead of leaving empty
// columns on the right — grid auto-placement alone can't do that.
const ROW_SIZE = 5
const rows = computed(() => {
  const chunks = []
  for (let i = 0; i < logos.length; i += ROW_SIZE) {
    chunks.push(logos.slice(i, i + ROW_SIZE))
  }
  return chunks
})
</script>

<template>
  <section class="section attendees">
    <div class="container">
      <div class="attendees__panel">
        <h2 class="attendees__title">Past Attendees Include</h2>
        <div class="attendees__rows">
          <ul
              v-for="(row, i) in rows"
              :key="i"
              class="attendees__grid"
              :style="{ '--cols': row.length }"
          >
            <li v-for="logo in row" :key="logo.name" class="attendees__logo">
              <img loading="lazy"
                  v-if="logo.src"
                  :src="logo.src"
                  :alt="logo.name"
                  decoding="async"
                  width="120"
                  height="32"
              />
              <span v-else>{{ logo.name }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.attendees__panel {
  background: #121b2666;
  border-radius: 24px;
  padding: 36px 56px 56px 56px;
  display: flex;
  flex-direction: column;
  gap: 56px;
}
.attendees__title {
  font-family: 'Manrope', sans-serif;
  text-align: center;
  font-size: 48px;
  font-weight: 700;
  font-style: normal;
  margin: 0;
}

.attendees__rows {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

/* Each row is its own grid with exactly as many columns as it has items,
   so a shorter last row (e.g. 4 items) stretches across the full width
   instead of sitting in 4 of 5 columns with a gap on the right. */
.attendees__grid {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(var(--cols), 1fr);
  gap: 16px;
}
.attendees__logo {
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  background: rgba(255, 255, 255, 0.01);
  min-height: 76px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 20px;
}
.attendees__logo img {
  max-width: 100%;
  max-height: 67px;
  width: auto;
  height: auto;
  object-fit: contain;
  filter: brightness(0) invert(1);
  opacity: 0.9;
}
.attendees__logo span {
  font-weight: 700;
  font-size: 13px;
  color: var(--text-dim);
  text-transform: uppercase;
  letter-spacing: 0.02em;
}

@media (max-width: 1024px) {
  .attendees__panel {
    padding: 28px;
    gap: 32px;
  }
  /* On tablet/mobile, row-based columns would create awkward uneven
     widths (e.g. a 4-wide row next to 3-wide rows). Collapse back to a
     single uniform grid instead. */
  .attendees__rows {
    display: contents;
  }
  .attendees__grid {
    display: contents;
  }
  .attendees__panel > .attendees__rows {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }
}
@media (max-width: 640px) {
  .attendees__panel {
    padding: 20px;
    gap: 24px;
    border-radius: var(--radius-md);
  }
  .attendees__panel > .attendees__rows {
    grid-template-columns: repeat(2, 1fr);
  }
  .attendees__title {
    font-size: 24px;
  }
}
</style>