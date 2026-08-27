<script setup>
import { computed, ref } from 'vue'
import enterpriseImg from '../assets/images/logo.svg'
import serviceImg from '../assets/images/logo.svg'
import gamedevImg from '../assets/images/logo.svg'
import aiNativeImg from '../assets/images/logo.svg'
import startup1 from '../assets/images/logo.svg'
import startup2 from '../assets/images/logo.svg'
import startup3 from '../assets/images/logo.svg'
import startup4 from '../assets/images/logo.svg'
import startup5 from '../assets/images/logo.svg'
import bridge1 from '../assets/images/logo.svg'
import bridge2 from '../assets/images/logo.svg'
import bridge3 from '../assets/images/logo.svg'
import bridge4 from '../assets/images/logo.svg'
import bridge5 from '../assets/images/logo.svg'

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
</script>

<template>
  <section id="tracks" class="section tabs">
    <div class="container">
      <p class="tabs__kicker">Enterprise Uzbekistan Summit - Premium Dark</p>

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
          <img class="tabs__feature-media" :src="active.image" :alt="active.title" width="480" height="300" loading="lazy" decoding="async" />
          <div class="tabs__feature-body">
            <p class="tabs__feature-desc">{{ active.description }}</p>
            <ul class="tabs__feature-points">
              <li v-for="(p, i) in active.points" :key="i">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="10" fill="var(--accent-soft)" /><path d="M7 12.5l3 3 7-7" stroke="var(--accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" /></svg>
                <span>{{ p }}</span>
              </li>
            </ul>
            <p class="tabs__feature-ideal"><span>Ideal for:</span> {{ active.idealFor }}</p>
          </div>
        </div>
      </template>

      <template v-else>
        <div class="tabs__grid">
          <article v-for="card in active.cards" :key="card.title" class="tabs__card">
            <img class="tabs__card-media" :src="card.image" :alt="card.title" width="277" height="150" loading="lazy" decoding="async" />
            <h3>{{ card.title }}</h3>
            <div class="tabs__card-meta">
              <span>{{ card.date }}</span>
              <span>{{ card.time }}</span>
              <span>{{ card.place }}</span>
            </div>
            <p>{{ card.desc }}</p>
            <p v-if="card.ideal" class="tabs__card-ideal"><span>Ideal for:</span> {{ card.ideal }}</p>
          </article>
        </div>
      </template>
    </div>
  </section>
</template>

<style scoped>
.tabs__kicker {
  color: var(--text-faint);
  font-size: 12px;
  margin: 0 0 16px;
}
.tabs__pills {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 24px;
}
.tabs__title {
  font-size: 32px;
  margin: 0 0 20px;
}
.tabs__meta {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  margin-bottom: 24px;
}
.tabs__meta span {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border);
  border-radius: 999px;
  padding: 8px 16px;
  font-size: 13px;
  color: var(--text-dim);
}
.tabs__meta svg {
  color: var(--accent);
  flex-shrink: 0;
}

.tabs__feature {
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 28px;
  display: grid;
  grid-template-columns: 0.85fr 1.15fr;
  gap: 28px;
}
.tabs__feature-media {
  border-radius: var(--radius-md);
  min-height: 220px;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border: 1px solid var(--border);
}
.tabs__feature-desc {
  color: var(--text);
  font-size: 16px;
  line-height: 1.5;
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
  font-size: 14px;
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
  font-size: 13px;
  color: var(--text-dim);
  margin: 0;
}
.tabs__feature-ideal span {
  color: var(--text);
  font-weight: 600;
}

.tabs__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 18px;
}
.tabs__card {
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
  .tabs__feature {
    grid-template-columns: 1fr;
  }
  .tabs__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (max-width: 640px) {
  .tabs__title {
    font-size: 24px;
  }
  .tabs__feature {
    padding: 18px;
  }
  .tabs__grid {
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