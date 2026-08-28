<script setup>
import { computed, ref } from 'vue'
import enterpriseImg from '../assets/images/Event_image.webp'
import serviceImg from '../assets/images/Event_image.webp'
import gamedevImg from '../assets/images/photo-16.webp'
import aiNativeImg from '../assets/images/photo-17.webp'
import startup1 from '../assets/images/photo-5.webp'
import startup2 from '../assets/images/photo-6.webp'
import startup3 from '../assets/images/photo-7.webp'
import startup4 from '../assets/images/photo-8.webp'
import startup5 from '../assets/images/photo-9.webp'
import bridge1 from '../assets/images/photo-10.webp'
import bridge2 from '../assets/images/photo-11.webp'
import bridge3 from '../assets/images/photo-12.webp'
import bridge4 from '../assets/images/photo-13.webp'
import bridge5 from '../assets/images/photo-14.webp'
import Cursor from '../assets/images/Cursor.webp'

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
        <!-- Pills -->
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

        <!-- FEATURE type -->
        <template v-if="active.type === 'feature'">
          <div class="tabs__meta">
            <span>
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <rect x="3" y="5" width="18" height="16" rx="2" stroke="currentColor" stroke-width="1.6" />
                <path d="M3 9h18M8 3v4M16 3v4" stroke="currentColor" stroke-width="1.6" />
              </svg>
              {{ active.date }}
            </span>
            <span>
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <circle cx="12" cy="12" r="9" stroke="currentColor" stroke-width="1.6" />
                <path d="M12 7v5l3 2" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" />
              </svg>
              {{ active.time }}
            </span>
            <span>
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M12 21s7-6.2 7-11a7 7 0 10-14 0c0 4.8 7 11 7 11z" stroke="currentColor" stroke-width="1.6" />
                <circle cx="12" cy="10" r="2.4" stroke="currentColor" stroke-width="1.6" />
              </svg>
              {{ active.place }}
            </span>
          </div>

          <div class="tabs__feature">
            <div class="tabs__feature-media-wrap">
              <img
                  class="tabs__feature-media"
                  :src="active.image"
                  :alt="active.title"
                  width="480"
                  height="300"
                  loading="lazy"
                  decoding="async"
              />
              <div v-if="active.imageOverlay" class="tabs__feature-overlay">
                <h3>{{ active.imageOverlay.title }}</h3>
                <p>{{ active.imageOverlay.text }}</p>
                <button type="button" class="tabs__feature-cta">
                  {{ active.imageOverlay.cta }}
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                    <path d="M5 12h14M13 6l6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                  </svg>
                </button>
              </div>
              <img
                  v-if="active.imageOverlay"
                  class="tabs__feature-cursor"
                  :src="Cursor"
                  alt=""
                  aria-hidden="true"
                  width="22"
                  height="22"
              />
            </div>

            <div class="tabs__feature-body">
              <p class="tabs__feature-desc">{{ active.description }}</p>
              <ul class="tabs__feature-points">
                <li v-for="(p, i) in active.points" :key="i">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                    <circle cx="12" cy="12" r="10" fill="var(--accent-2)" />
                    <path d="M7 12.5l3 3 7-7" stroke="var(--panel-2)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                  </svg>
                  <span>{{ p }}</span>
                </li>
              </ul>
              <p class="tabs__feature-ideal">
                <span>Ideal for:</span> {{ active.idealFor }}
              </p>
            </div>
          </div>
        </template>

        <!-- GRID type -->
        <template v-else>
          <div class="tabs__rows">
            <div
                v-for="(row, i) in cardRows"
                :key="i"
                class="tabs__grid"
                :style="{ '--cols': row.length }"
            >
              <article v-for="card in row" :key="card.title" class="tabs__card">
                <img
                    class="tabs__card-media"
                    :src="card.image"
                    :alt="card.title"
                    width="277"
                    height="150"
                    loading="lazy"
                    decoding="async"
                />
                <h3>{{ card.title }}</h3>
                <div class="tabs__card-meta">
                  <span>
                    <svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                      <rect x="3" y="5" width="18" height="16" rx="2" stroke="currentColor" stroke-width="1.8" />
                      <path d="M3 9h18M8 3v4M16 3v4" stroke="currentColor" stroke-width="1.8" />
                    </svg>
                    {{ card.date }}
                  </span>
                  <span>
                    <svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                      <circle cx="12" cy="12" r="9" stroke="currentColor" stroke-width="1.8" />
                      <path d="M12 7v5l3 2" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
                    </svg>
                    {{ card.time }}
                  </span>
                  <span>
                    <svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                      <path d="M12 21s7-6.2 7-11a7 7 0 10-14 0c0 4.8 7 11 7 11z" stroke="currentColor" stroke-width="1.8" />
                      <circle cx="12" cy="10" r="2.4" stroke="currentColor" stroke-width="1.8" />
                    </svg>
                    {{ card.place }}
                  </span>
                </div>
                <p>{{ card.desc }}</p>
                <p v-if="card.ideal" class="tabs__card-ideal">
                  <span>Ideal for:</span> {{ card.ideal }}
                </p>
              </article>
            </div>
          </div>
        </template>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* ========== BASE ========== */
.tabs__panel {
  background: #121b2666;
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 40px 40px 48px;
  display: flex;
  flex-direction: column;
  gap: 32px;
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
  line-height: 1.1;
  margin: 0;
}

/* Meta bar */
.tabs__meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: 999px;
  padding: 4px 8px;
}
.tabs__meta span {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  font-size: 13px;
  color: #ffffff;
  white-space: nowrap;
}
.tabs__meta svg {
  color: var(--accent);
  flex-shrink: 0;
}

/* Feature block */
.tabs__feature {
  background:
      linear-gradient(0deg, rgba(255, 255, 255, 0.031), rgba(255, 255, 255, 0.031)),
      linear-gradient(180deg, rgba(132, 255, 193, 0.02) 0%, rgba(132, 255, 193, 0.016) 84.62%),
      radial-gradient(53.18% 100% at 51.72% 0%, rgba(132, 255, 193, 0.08) 0%, transparent 100%);
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
  background: linear-gradient(180deg, rgba(0, 6, 14, 0.92) 0%, rgba(0, 6, 14, 0.55) 45%, transparent 75%);
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
  line-height: 1.45;
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
  font-size: 16px;
  color: var(--text-dim);
  margin: 0;
}
.tabs__feature-ideal span {
  color: var(--text);
  font-weight: 600;
}

/* Grid cards */
.tabs__rows {
  display: flex;
  flex-direction: column;
  gap: 18px;
}
.tabs__grid {
  display: grid;
  grid-template-columns: repeat(var(--cols), 1fr);
  gap: 18px;
}
.tabs__card {
  background:
      linear-gradient(0deg, rgba(255, 255, 255, 0.031), rgba(255, 255, 255, 0.031)),
      linear-gradient(180deg, rgba(132, 255, 193, 0.02) 0%, rgba(132, 255, 193, 0.016) 84.62%),
      radial-gradient(53.18% 100% at 51.72% 0%, rgba(132, 255, 193, 0.08) 0%, transparent 100%);
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
  line-height: 1.3;
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

/* ========== TABLET ≤ 1024px ========== */
@media (max-width: 1024px) {
  .tabs__panel {
    padding: 28px;
    gap: 24px;
  }

  .tabs__title {
    font-size: 36px;
  }

  .tabs__feature {
    grid-template-columns: 1fr;
    padding: 20px;
    gap: 20px;
  }

  .tabs__feature-media-wrap {
    min-height: 240px;
    height: auto;
    aspect-ratio: 16 / 10;
  }

  /* Grid: 2 ustun */
  .tabs__grid {
    grid-template-columns: repeat(2, 1fr) !important;
  }
}

/* ========== MOBILE ≤ 640px ========== */
@media (max-width: 640px) {
  .tabs__panel {
    padding: 16px;
    gap: 20px;
    border-radius: 16px;
  }

  /* Pills — horizontal scroll */
  .tabs__pills {
    flex-wrap: nowrap;
    overflow-x: auto;
    gap: 8px;
    margin: 0 -16px;
    padding: 0 16px 8px;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none; /* Firefox */
  }
  .tabs__pills::-webkit-scrollbar {
    display: none; /* Chrome/Safari */
  }
  .tabs__pills .pill {
    flex-shrink: 0;
    white-space: nowrap;
  }

  .tabs__title {
    font-size: 22px;
    line-height: 1.25;
  }

  /* Meta — vertical stack */
  .tabs__meta {
    flex-direction: column;
    align-items: stretch;
    border-radius: 16px;
    padding: 6px;
    gap: 2px;
  }
  .tabs__meta span {
    padding: 10px 12px;
    font-size: 13px;
    white-space: normal;
    border-radius: 10px;
  }
  .tabs__meta span + span {
    border-top: 1px solid rgba(255, 255, 255, 0.06);
  }

  /* Feature */
  .tabs__feature {
    padding: 14px;
    gap: 16px;
    border-radius: 16px;
  }
  .tabs__feature-media-wrap {
    min-height: 180px;
    aspect-ratio: 16 / 11;
  }
  .tabs__feature-overlay {
    padding: 16px;
    gap: 8px;
  }
  .tabs__feature-overlay h3 {
    font-size: 16px;
  }
  .tabs__feature-overlay p {
    font-size: 12px;
  }
  .tabs__feature-cta {
    font-size: 13px;
    padding: 8px 14px;
  }
  .tabs__feature-cursor {
    display: none; /* mobilada kerak emas */
  }

  .tabs__feature-desc {
    font-size: 15px;
    line-height: 1.45;
    margin-bottom: 14px;
  }
  .tabs__feature-points {
    gap: 12px;
    margin-bottom: 16px;
  }
  .tabs__feature-points li {
    font-size: 14px;
  }
  .tabs__feature-ideal {
    font-size: 14px;
    padding: 10px 12px;
  }

  /* Cards — 1 ustun */
  .tabs__rows {
    gap: 14px;
  }
  .tabs__grid {
    grid-template-columns: 1fr !important;
    gap: 14px;
  }
  .tabs__card {
    padding: 14px;
  }
  .tabs__card-media {
    height: 140px;
  }
  .tabs__card h3 {
    font-size: 15px;
  }
  .tabs__card-meta {
    gap: 8px;
    font-size: 11px;
  }
  .tabs__card p {
    font-size: 13px;
  }
}
</style>