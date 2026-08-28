<script setup>
import { computed, ref } from 'vue'
import enterpriseImg from '../assets/images/Event_image.png'
import serviceImg from '../assets/images/Event_image.png'
import gamedevImg from '../assets/images/photo-16.png'
import aiNativeImg from '../assets/images/photo-17.jpg'
import startup1 from '../assets/images/photo-5.png'
import startup2 from '../assets/images/photo-6.png'
import startup3 from '../assets/images/photo-7.jpg'
import startup4 from '../assets/images/photo-8.png'
import startup5 from '../assets/images/photo-9.jpg'
import bridge1 from '../assets/images/photo-10.jpg'
import bridge2 from '../assets/images/photo-11.jpg'
import bridge3 from '../assets/images/photo-12.jpg'
import bridge4 from '../assets/images/photo-13.png'
import bridge5 from '../assets/images/photo-14.jpg'
import Cursor from '../assets/images/Cursor.svg'

// NOTE: `serviceImg` va `enterpriseImg` hozircha bir xil placeholder
// (Event_image.png) fayldan import qilinyapti. Har ikkalasi uchun
// `imageOverlay` matni (sarlavha/tavsif/tugma) rasm ustiga chiziladi —
// asl rasm fayllarini almashtirsangiz ham overlay o'zgarishsiz qoladi.

const tracks = [
  {
    id: 'enterprise',
    label: 'Enterprise Uzbekistan',
    type: 'feature',
    image: enterpriseImg,
    title: 'Enterprise Uzbekistan Summit',
    date: 'September 23, 2026',
    time: '10:00 - 12:00',
    place: 'CAEx, Hall 1',
    description: "Discover Enterprise Uzbekistan — the country's first dedicated jurisdiction built for global technology business.",
    imageOverlay: {
      title: 'Enterprise Uzbekistan Summit',
      text: 'Legally protected testing environment for new business models and frontier technologies.',
      cta: 'Register now'
    },
    points: [
      'Running on elements of English and Welsh law, it offers a legal environment that locks in the day you enter and remains guaranteed through 2100 — for IT exporters, data centers, startups, and infrastructure and institutional investors alike.',
      'On September 23, Enterprise Uzbekistan takes the stage at ICT Week to open the framework up in person. Meet the people building it, see how it\u2019s structured, and get a first look at what it means to operate inside it.',
      'Join us at CAEx, Main Hall — come see it before everyone else does.'
    ],
    idealFor: 'global tech companies, investors, legal and financial advisors, and government officials'
  },
  {
    id: 'startup',
    label: 'Startup & VC',
    type: 'grid',
    title: 'Startup & Venture Summit',
    // Figma: 1-qator 3 ta, 2-qator 2 ta (image 2)
    rowSizes: [3, 2],
    cards: [
      { title: 'Startup & Venture Summit', date: 'Sep 22, 2026', time: '14:00 - 17:00', place: 'CAEx, Main Hall', desc: "The flagship gathering of Central Asia's startup ecosystem — bringing together founders, investors and government leaders to discuss the region's next stage of growth.", image: startup1 },
      { title: 'Startup Blink Awards', date: 'Sep 23, 2026', time: '16:00 - 18:00', place: 'CAEx, Hall 3', desc: 'An official award ceremony celebrating the top-performing startup ecosystems and ecosystem builders shaping the global innovation landscape.', image: startup2 },
      { title: 'Startup World Cup - Uzbekistan Regional Final', date: 'Sep 24, 2026', time: '10:00 - 17:00', place: 'CAEx, Main Hall', desc: "The regional final of the world's largest startup competition, where top regional startups compete for a spot in the global final and a share of $1M+ in investment.", image: startup3 },
      { title: 'Ignyte Challenge', date: 'Sep 25, 2026', time: '11:00 - 13:00', place: 'CAEx, Hall 3', desc: 'A high-energy pitch competition in partnership with DIFC Innovation Hub and IGNYTE connecting ambitious startups with international investors and industry experts.', image: startup4 },
      { title: 'Taqdimot (Startup Pitches)', date: 'Sep 25, 2026', time: '14:00 - 17:00', place: 'CAEx, Hall 2', desc: 'Live pitch sessions showcasing promising global startups to investors, corporates and ecosystem partners, serving as a match-making platform.', image: startup5 }
    ]
  },
  {
    id: 'service',
    label: 'Service Companies',
    type: 'feature',
    image: serviceImg,
    title: 'Tech & Service Outsourcing Conference',
    date: 'September 23, 2026',
    time: '12:00 - 14:00',
    place: 'CAEx, Hall 3',
    description: 'Explore the future of global services and outsourcing from the heart of Central Asia. Discover why Uzbekistan is the next big outsourcing destination for ITES companies and investment.',
    imageOverlay: {
      title: 'Regulatory Sandbox',
      text: 'Legally protected testing environment for new business models and frontier technologies.',
      cta: 'Register now'
    },
    points: [
      'Insights into 0% tax breaks for companies',
      'Access a multilingual, tech-savvy workforce of 21 million+',
      'Special IT visa and 3-year zero-cost office support program'
    ],
    idealFor: 'outsourcing companies, IT leaders, global service providers, investors, and government officials'
  },
  {
    id: 'bridge',
    label: 'Global Bridge',
    type: 'grid',
    title: 'Global Bridge',
    // Figma: 1-qator 2 ta (kengroq kartalar), 2-qator 3 ta (image 4)
    rowSizes: [2, 3],
    cards: [
      { title: 'Uzbek-Japan Digital Community Forum', date: 'September 22, 2026', time: '15:00 - 18:00', place: 'CAEx, Hall 3', desc: 'Explore new opportunities for collaboration between Uzbekistan and Japan in the ICT sector, from joint software development to talent exchange and market entry support.', ideal: 'Japanese tech companies, IT leaders, government officials and investors', image: bridge1 },
      { title: 'OTS Technology Forum', date: 'September 23, 2026', time: '12:00 - 14:00', place: 'CAEx, Hall 2', desc: 'The forum unites key stakeholders from the Organization of Turkic States (OTS) to advance cooperation in digital innovation and startup ecosystems.', ideal: 'Government representatives, technology parks, innovation agencies, startup ecosystem leaders, investors, founders', image: bridge2 },
      { title: 'Uzbekistan - Middle East Tech Summit', date: 'Sep 24, 2026', time: '14:00 - 16:30', place: 'IT Park Complex', desc: "The Summit connects Uzbekistan's tech ecosystem with Middle Eastern investors to expand IT infrastructure and unlock new growth in the MENA region.", ideal: 'Investment into Uzbekistan IT and digital infrastructure sector', image: bridge3 },
      { title: 'Sabriya: Women in Digital Economy', date: 'Sep 24, 2026', time: '14:00 - 16:30', place: 'CAEx, Hall 3', desc: "Discover Sabriya — IT Park's initiative empowering women to lead and grow in the digital economy across Uzbekistan and beyond.", ideal: 'Women entrepreneurs, developers, investors and ecosystem partners', image: bridge4 },
      { title: 'AWS Community Day', date: 'Sep 25, 2026', time: '10:00 - 17:00', place: 'CAEx, Main Hall', desc: 'Join a full day of technology talks and hands-on sessions led by AWS experts and the regional developer community.', ideal: 'Developers, cloud architects, DevOps engineers and IT leaders', image: bridge5 }
    ]
  },
  {
    id: 'gamedev',
    label: 'Gamedev',
    type: 'feature',
    image: gamedevImg,
    title: 'GameGap: GameDev Conference',
    date: 'September 25, 2026',
    time: '14:00 - 17:00',
    place: 'CAEx, Hall 3',
    description: "Discover the future of gaming from the heart of Central Asia. Explore why Uzbekistan's GameDev ecosystem is becoming a key hub for studios, publishers and investors in the region.",
    points: [
      'Insights from world-class gaming industry experts',
      'Access to a growing regional talent pool and gaming market',
      'Networking with publishers, investors and studio founders'
    ],
    idealFor: 'game developers, publishers, investors, gaming executives and industry professionals'
  },
  {
    id: 'ai',
    label: 'AI Native',
    type: 'feature',
    image: aiNativeImg,
    title: 'AI Native: Ideas to Innovation',
    date: 'September 24, 2026',
    time: '10:00 – 12:15',
    place: 'CAEx, Hall 3',
    description: 'Step into a world where AI thinks, speaks, creates, and moves — from intelligent agents and LLMs to cloud technologies and real-world robotics.',
    points: [
      'Experience LLMs and cloud AI in action with live, hands-on demos',
      'See robotics on stage — from working prototypes to AI built for real jobs',
      'Step into the arena yourself with "Join the AI Game" and discover study programs, career opportunities, and hackathons'
    ],
    idealFor: 'AI developers, tech founders, robotics innovators, enterprise IT leaders, and students'
  }
]

const activeId = ref(tracks[0].id)
const active = computed(() => tracks.find((t) => t.id === activeId.value))

// Cards render as their own per-row grid so a partial last row stretches
// to fill the full width instead of leaving an empty gap. Row sizes are
// defined per track (rowSizes) to exactly match the Figma layout for
// that section — different tracks split their cards differently
// (e.g. Startup & VC = 3 then 2, Global Bridge = 2 then 3). Falls back
// to a uniform chunk-of-3 split if a track doesn't define rowSizes.
const DEFAULT_ROW_SIZE = 3
const cardRows = computed(() => {
  if (active.value.type !== 'grid') return []
  const cards = active.value.cards
  const sizes = active.value.rowSizes

  if (sizes && sizes.reduce((a, b) => a + b, 0) === cards.length) {
    const rows = []
    let offset = 0
    for (const size of sizes) {
      rows.push(cards.slice(offset, offset + size))
      offset += size
    }
    return rows
  }

  // fallback: chunk of DEFAULT_ROW_SIZE
  const chunks = []
  for (let i = 0; i < cards.length; i += DEFAULT_ROW_SIZE) {
    chunks.push(cards.slice(i, i + DEFAULT_ROW_SIZE))
  }
  return chunks
})
</script>

<template>
  <section id="tracks" class="section tabs">
    <div class="container">
      <div class="tabs__panel" :class="{ 'tabs__panel--alt': active.id !== 'enterprise' }">
        <div class="tabs__pills" role="tablist" aria-label="Event tracks">
          <button
              v-for="t in tracks"
              :key="t.id"
              type="button"
              role="tab"
              class="pill"
              :class="{ active: t.id === activeId }"
              :aria-selected="t.id === activeId"
              @click="activeId = t.id"
          >
            {{ t.label.toUpperCase() }}
          </button>
        </div>

        <h2 class="tabs__title">{{ active.title.toUpperCase() }}</h2>

        <template v-if="active.type === 'feature'">
          <div class="tabs__meta">
            <span><svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true"><rect x="3" y="5" width="18" height="16" rx="2" stroke="currentColor" stroke-width="1.6" /><path d="M3 9h18M8 3v4M16 3v4" stroke="currentColor" stroke-width="1.6" /></svg>{{ active.date }}</span>
            <span><svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="9" stroke="currentColor" stroke-width="1.6" /><path d="M12 7v5l3 2" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" /></svg>{{ active.time }}</span>
            <span><svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 21s7-6.2 7-11a7 7 0 10-14 0c0 4.8 7 11 7 11z" stroke="currentColor" stroke-width="1.6" /><circle cx="12" cy="10" r="2.4" stroke="currentColor" stroke-width="1.6" /></svg>{{ active.place }}</span>
          </div>

          <div class="tabs__feature">
            <div class="tabs__feature-media-wrap">
              <img class="tabs__feature-media" :src="active.image" :alt="active.title" width="480" height="300" loading="lazy" decoding="async" />
              <div v-if="active.imageOverlay" class="tabs__feature-overlay">
                <h3>{{ active.imageOverlay.title }}</h3>
                <p>{{ active.imageOverlay.text }}</p>
                <button type="button" class="tabs__feature-cta">
                  {{ active.imageOverlay.cta }}
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M5 12h14M13 6l6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" /></svg>
                </button>
              </div>
              <img v-if="active.imageOverlay" class="tabs__feature-cursor" :src="Cursor" alt="" aria-hidden="true" width="22" height="22" />
            </div>
            <div class="tabs__feature-body">
              <p class="tabs__feature-desc">{{ active.description }}</p>
              <ul class="tabs__feature-points">
                <li v-for="(p, i) in active.points" :key="i">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="10" fill="var(--accent-2)" /><path d="M7 12.5l3 3 7-7" stroke="var(--panel-2)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" /></svg>
                  <span>{{ p }}</span>
                </li>
              </ul>
              <p class="tabs__feature-ideal"><span>Ideal for:</span> {{ active.idealFor }}</p>
            </div>
          </div>
        </template>

        <template v-else>
          <div class="tabs__rows">
            <div
                v-for="(row, i) in cardRows"
                :key="i"
                class="tabs__grid"
                :style="{ '--cols': row.length }"
            >
              <article v-for="card in row" :key="card.title" class="tabs__card">
                <img class="tabs__card-media" :src="card.image" :alt="card.title" width="277" height="150" loading="lazy" decoding="async" />
                <h3>{{ card.title }}</h3>
                <div class="tabs__card-meta">
                  <span><svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true"><rect x="3" y="5" width="18" height="16" rx="2" stroke="currentColor" stroke-width="1.8" /><path d="M3 9h18M8 3v4M16 3v4" stroke="currentColor" stroke-width="1.8" /></svg>{{ card.date }}</span>
                  <span><svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="9" stroke="currentColor" stroke-width="1.8" /><path d="M12 7v5l3 2" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" /></svg>{{ card.time }}</span>
                  <span><svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 21s7-6.2 7-11a7 7 0 10-14 0c0 4.8 7 11 7 11z" stroke="currentColor" stroke-width="1.8" /><circle cx="12" cy="10" r="2.4" stroke="currentColor" stroke-width="1.8" /></svg>{{ card.place }}</span>
                </div>
                <p>{{ card.desc }}</p>
                <p v-if="card.ideal" class="tabs__card-ideal"><span>Ideal for:</span> {{ card.ideal }}</p>
              </article>
            </div>
          </div>
        </template>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tabs__kicker {
  color: var(--text-faint);
  font-size: 12px;
  margin: 0 0 16px;
}

.tabs__panel {
  background: #121b2666;
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 40px 40px 48px 40px;
  display: flex;
  flex-direction: column;
  gap: 32px;
}
.tabs__panel--alt {
  background: #121b2666;
}

.tabs__pills {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.tabs__title {
  text-align: center;
  font-weight: 700;
  font-size: 56px;
  line-height: 110%;
  margin: 0;
}
.tabs__meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: 999px;
}
.tabs__meta span {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  font-size: 13px;
  color: #ffffff;
}
.tabs__meta svg {
  color: var(--accent);
  flex-shrink: 0;
}

.tabs__feature {
  background: linear-gradient(0deg, rgba(255, 255, 255, 0.0313726), rgba(255, 255, 255, 0.0313726)),
  linear-gradient(180deg, rgba(132, 255, 193, 0.02) 0%, rgba(132, 255, 193, 0.016) 84.62%),
  radial-gradient(53.18% 100% at 51.72% 0%, rgba(132, 255, 193, 0.08) 0%, rgba(255, 255, 255, 0) 100%);

  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  display: grid;
  grid-template-columns: 0.85fr 1.15fr;
  gap: 28px;
}
.tabs__feature-media-wrap {
  position: relative;
  border-radius: var(--radius-md);
  overflow: hidden;
  min-height: 220px;
  height: 100%;
  border: 1px solid var(--border);
}
.tabs__feature-media {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.tabs__feature-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 10px;
  padding: 24px;
  background: linear-gradient(180deg, rgba(0, 6, 14, 0.92) 0%, rgba(0, 6, 14, 0.55) 45%, rgba(0, 6, 14, 0) 75%);
}
.tabs__feature-cursor {
  position: absolute;
  top: 45%;
  left: 68%;
  filter: drop-shadow(0 2px 3px rgba(0, 0, 0, 0.5));
  pointer-events: none;
}
.tabs__feature-overlay h3 {
  color: #fff;
  font-size: 20px;
  margin: 0;
}
.tabs__feature-overlay p {
  color: rgba(255, 255, 255, 0.85);
  font-size: 13px;
  line-height: 1.5;
  margin: 0;
}
.tabs__feature-cta {
  align-self: flex-start;
  margin-top: auto;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--accent);
  color: #04140c;
  font-weight: 600;
  font-size: 14px;
  border: none;
  border-radius: 999px;
  padding: 10px 18px;
  cursor: pointer;
}
.tabs__feature-desc {
  color: #ffffff;
  font-size: 18px;
  line-height: 26px;
  font-weight: 600;
  margin: 0 0 18px;
}
.tabs__feature-points {
  list-style: none;
  margin: 0 0 20px;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 14px;
}
.tabs__feature-points li {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  color: var(--text-dim);
  font-size: 16px;
  line-height: 1.5;
}
.tabs__feature-points svg {
  flex-shrink: 0;
  margin-top: 2px;
}
.tabs__feature-ideal {
  border-left: 3px solid var(--accent);
  padding: 10px 14px;
  background: rgba(255, 255, 255, 0.02);
  border-radius: 0 8px 8px 0;
  font-size: 18px;
  color: var(--text-dim);
  margin: 0;
}
.tabs__feature-ideal span {
  color: var(--text);
  font-weight: 600;
}

.tabs__rows {
  display: flex;
  flex-direction: column;
  gap: 18px;
}
/* Each row is its own grid with exactly as many columns as it has cards,
   so a shorter row (per the track's rowSizes) stretches across the full
   width instead of sitting in fewer columns with a gap on the right. */
.tabs__grid {
  display: grid;
  grid-template-columns: repeat(var(--cols), 1fr);
  gap: 18px;
}
.tabs__card {
  background: linear-gradient(0deg, rgba(255, 255, 255, 0.0313726), rgba(255, 255, 255, 0.0313726)),
  linear-gradient(180deg, rgba(132, 255, 193, 0.02) 0%, rgba(132, 255, 193, 0.016) 84.62%),
  radial-gradient(53.18% 100% at 51.72% 0%, rgba(132, 255, 193, 0.08) 0%, rgba(255, 255, 255, 0) 100%);

  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.tabs__card-media {
  border-radius: var(--radius-sm);
  height: 150px;
  width: 100%;
  object-fit: cover;
  border: 1px solid var(--border);
  margin-bottom: 6px;
}
.tabs__card h3 {
  font-size: 16px;
  margin: 0;
}
.tabs__card-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  font-size: 12px;
  color: var(--text-faint);
}
.tabs__card-meta span {
  display: inline-flex;
  align-items: center;
  gap: 5px;
}
.tabs__card-meta svg {
  color: var(--accent);
  flex-shrink: 0;
}
.tabs__card p {
  font-size: 13px;
  color: var(--text-dim);
  line-height: 1.5;
  margin: 4px 0 0;
}
.tabs__card-ideal span {
  color: var(--text);
  font-weight: 600;
}

@media (max-width: 1024px) {
  .tabs__panel {
    padding: 28px;
  }
  .tabs__feature {
    grid-template-columns: 1fr;
  }
  /* Row-based columns get awkward once cards wrap to 2-up; collapse to a
     single uniform 2-column grid instead. */
  .tabs__rows {
    display: contents;
  }
  .tabs__grid {
    display: contents;
  }
  .tabs__panel > .tabs__rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
  }
}
@media (max-width: 640px) {
  .tabs__title {
    font-size: 24px;
  }
  .tabs__panel {
    padding: 18px;
  }
  .tabs__panel > .tabs__rows {
    grid-template-columns: 1fr;
  }
  .tabs__pills {
    flex-wrap: nowrap;
    overflow-x: auto;
    padding-bottom: 6px;
    margin-left: -18px;
    margin-right: -18px;
    padding-left: 18px;
    padding-right: 18px;
  }
}
</style>