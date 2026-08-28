<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import heroVideo from '../assets/images/video.mp4'
import photo1 from '../assets/images/photo-1.webp'
import photo2 from '../assets/images/photo-2.webp'
import photo3 from '../assets/images/photo-3.webp'
import StartupBlink from '../assets/images/StartupBlink.webp'
import Vector from '../assets/images/Vector.webp'
import Uzum from '../assets/images/uzum.webp'
import TbcBank from '../assets/images/tbc.webp'

const EVENT_DATE = new Date('2026-10-01T00:00:00Z')
const days = ref(0)
const hours = ref(0)
const minutes = ref(0)
let timer = null

const videoEl = ref(null)
const isPlaying = ref(false)

function updateCountdown() {
  const diff = Math.max(0, EVENT_DATE.getTime() - Date.now())
  days.value = Math.floor(diff / (1000 * 60 * 60 * 24))
  hours.value = Math.floor((diff / (1000 * 60 * 60)) % 24)
  minutes.value = Math.floor((diff / (1000 * 60)) % 60)
}

function startTimer() {
  if (timer) return
  updateCountdown()
  timer = setInterval(updateCountdown, 30000)
}
function stopTimer() {
  clearInterval(timer)
  timer = null
}

function handleVisibilityChange() {
  if (document.hidden) {
    stopTimer()
  } else {
    startTimer()
  }
}

onMounted(() => {
  startTimer()
  document.addEventListener('visibilitychange', handleVisibilityChange)
})
onUnmounted(() => {
  stopTimer()
  document.removeEventListener('visibilitychange', handleVisibilityChange)
})

function scrollToRegister() {
  document.getElementById('register')?.scrollIntoView({ behavior: 'smooth' })
}

function togglePlay() {
  const video = videoEl.value
  if (!video) return
  if (video.paused) {
    video.play()
    isPlaying.value = true
  } else {
    video.pause()
    isPlaying.value = false
  }
}
function handleEnded() {
  isPlaying.value = false
}
</script>

<template>
  <section id="top" class="hero">
    <div class="container">
      <div class="hero__header">
        <h1 class="hero__title">Unlock the World's Fastest Growing Ecosystem</h1>
      </div>

      <div class="hero__grid">
        <div class="hero__media">
          <video
              ref="videoEl"
              :src="heroVideo"
              class="hero__video"
              preload="metadata"
              playsinline
              loop
              @click="togglePlay"
              @ended="handleEnded"
          ></video>
          <div class="hero__media-inner" :class="{ 'is-hidden': isPlaying }">
            <button
                type="button"
                class="hero__play"
                :aria-label="isPlaying ? 'Pause highlight video' : 'Play highlight video'"
                @click="togglePlay"
            >
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M6 4l14 8-14 8V4z" fill="#062015" />
              </svg>
            </button>
          </div>
        </div>

        <aside class="hero__card">
          <div class="hero__card-preview">
            <img
                :src="photo1"
                alt="ICT Week 2026 highlight photo"
                width="360"
                height="130"
                decoding="async"
            />
          </div>
          <p class="hero__card-text">
            learn everything about the thriving uzbek tech ecosystem — in just one week
          </p>
          <div class="hero__card-actions">
            <button type="button" class="btn btn-primary" @click="scrollToRegister">Register now</button>
            <a href="#tracks" class="btn btn-outline">
              Full agenda
              <svg width="12" height="12" viewBox="0 0 12 12" fill="none" aria-hidden="true">
                <path d="M2 10L10 2M10 2H4M10 2v6" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </a>
          </div>
          <div class="hero__countdown">
            <div class="hero__countdown-item">
              <strong>{{ days }}</strong>
              <span>DAYS</span>
            </div>
            <div class="hero__countdown-item">
              <strong>{{ hours }}</strong>
              <span>HOURS</span>
            </div>
            <div class="hero__countdown-item">
              <strong>{{ minutes }}</strong>
              <span>MINUTES</span>
            </div>
          </div>
        </aside>
      </div>

      <div class="hero__stats">
        <div class="hero__badge">
          <img
              :src="photo2"
              alt="ICT Week 2026 medal"
              width="150"
              height="150"
              decoding="async"
          />
        </div>

        <!-- Card 1 -->
        <div class="hero__stat-card">
          <span class="hero__stat-year">2026</span>
          <div class="hero__stat-row">
            <div class="hero__stat">
              <strong>$4.3B</strong>
              <span>Startup Ecosystem Valuation</span>
            </div>
            <div class="hero__stat">
              <strong>#1</strong>
              <span>In venture investment growth globally</span>
            </div>
          </div>
          <span class="hero__stat-source">
            <img :src="photo3" alt="Source" width="92" height="22" decoding="async" />
          </span>
        </div>

        <!-- Card 2 -->
        <div class="hero__stat-card">
          <span class="hero__stat-year">2026</span>
          <div class="hero__stat-row">
            <div class="hero__stat">
              <strong>#1</strong>
              <span>Ecosystem in the World by Growth Rate</span>
            </div>
            <div class="hero__stat">
              <strong>#1</strong>
              <span>Startup Hub in Central Asia (Tashkent)</span>
            </div>
          </div>
          <span class="hero__stat-source">
            <img :src="StartupBlink" alt="StartupBlink" width="92" height="22" decoding="async" />
          </span>
        </div>

        <!-- Card 3 — Fintech Unicorns -->
        <div class="hero__stat-card hero__stat-card--unicorn">
          <span class="hero__stat-year">2026</span>
          <div class="hero__stat-row hero__stat-row--unicorn">
            <div class="hero__stat">
              <strong class="hero__unicorn-num">
                2
                <img :src="Vector" alt="" width="28" height="30" decoding="async" />
              </strong>
              <span>Fintech Unicorns</span>
            </div>
          </div>
          <span class="hero__stat-source hero__stat-source--logos">
            <img :src="Uzum" alt="Uzum" width="80" height="20" decoding="async" />
            <img :src="TbcBank" alt="TBC Bank" width="80" height="20" decoding="async" />
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: 48px 0 0;
}

.hero__header {
  width: 100%;
  display: flex;
  justify-content: center;
  padding: 20px 0;
}

.hero__title {
  font-family: Manrope, sans-serif;
  text-align: center;
  font-size: 70px;
  line-height: 1.08;
  font-weight: 700;
  width: 945px;
  max-width: 100%;
  margin: 0 0 36px;
}

.hero__grid {
  display: grid;
  grid-template-columns: 1.65fr 1fr;
  gap: 20px;
  align-items: stretch;
}

.hero__media {
  position: relative;
  border-radius: var(--radius-lg);
  overflow: hidden;
  min-height: 340px;
  border: 1px solid var(--border);
  background: #0b1310;
}
.hero__video {
  width: 100%;
  height: 100%;
  min-height: 340px;
  object-fit: cover;
  display: block;
  cursor: pointer;
}
.hero__media-inner {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  transition: opacity 0.2s ease;
}
.hero__media-inner.is-hidden {
  opacity: 0;
}
.hero__play {
  width: 54px;
  height: 54px;
  border-radius: 50%;
  border: 0.64px solid rgba(255, 255, 255, 0.35);
  background: linear-gradient(180deg, var(--accent-2), var(--accent));
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  pointer-events: auto;
  box-shadow: 0 0 0 10px rgba(62, 224, 138, 0.14);
  transition: transform 0.15s ease;
}
.hero__play:hover {
  transform: scale(1.06);
}

.hero__card {
  background: #121B2666;
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 20px;
  backdrop-filter: blur(8px);
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.hero__card-preview {
  border-radius: var(--radius-md);
  width: 100%;
  height: 250px;
  overflow: hidden;
  background: linear-gradient(160deg, #0e1a15, #142621 60%, #0e1a15);
  border: 1px solid var(--border);
}
.hero__card-preview img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.hero__card-text {
  margin: 0;
  color: #ffffff;
  font-size: 22px;
  font-weight: 500;
  line-height: 1.5;
}
.hero__card-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}
.hero__card-actions .btn-outline {
  border-color: rgba(107, 230, 168, 0.35);
  color: var(--accent-2);
}
.hero__card-actions .btn-outline:hover {
  border-color: rgba(107, 230, 168, 0.6);
  background: rgba(62, 224, 138, 0.06);
}

.hero__countdown {
  margin-top: auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
.hero__countdown-item {
  background: rgba(18, 27, 38, 0.5);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-sm);
  padding: 14px 6px;
  text-align: center;
}
.hero__countdown-item strong {
  display: block;
  font-size: 36px;
  font-weight: 700;
  color: #ffffff;
}
.hero__countdown-item span {
  font-family: Manrope, sans-serif;
  font-size: 18px;
  font-weight: 500;
  color: var(--accent-2);
}

/* ========== STATS ========== */
.hero__stats {
  margin-top: 20px;
  display: grid;
  grid-template-columns: auto repeat(3, 1fr);
  gap: 14px;
  align-items: stretch;
  background: #121B2666;
  backdrop-filter: blur(15px);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 20px;
}
.hero__badge {
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero__badge img {
  max-width: 140px;
  height: auto;
}

.hero__stat-card {
  position: relative;
  border: 1.2px solid transparent;
  border-radius: var(--radius-md);
  background:
      linear-gradient(180deg, rgba(11, 16, 24, 0.96) 0%, rgba(11, 16, 24, 0.9) 100%) padding-box,
      linear-gradient(270deg, rgba(21, 91, 127, 1) 0%, rgba(27, 219, 134, 1) 100%) border-box;
  padding: 18px 16px 40px; /* pastki qismda source uchun joy */
  overflow: hidden;
  min-height: 140px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero__stat-year {
  position: absolute;
  top: 0;
  right: 0;
  background: rgba(132, 255, 193, 1);
  color: rgba(18, 27, 38);
  font-size: 14px;
  font-weight: 700;
  padding: 5px 14px;
  border-bottom-left-radius: var(--radius-sm);
  z-index: 2;
}

.hero__stat-row {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.hero__stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1;
  min-width: 0;
}

.hero__stat strong {
  display: flex;
  align-items: center;
  gap: 6px;
  font-family: Manrope, sans-serif;
  font-weight: 700;
  font-size: 28px;
  color: #ffffff;
  line-height: 1.1;
}

.hero__stat span {
  font-family: Manrope, sans-serif;
  font-weight: 500;
  font-size: 12px;
  line-height: 1.3;
  color: rgba(255, 255, 255, 0.75);
  max-width: none; /* eski 100px cheklov olib tashlandi */
}

.hero__stat-source {
  position: absolute;
  right: 14px;
  bottom: 12px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 6px;
}

/* Unicorn card maxsus */
.hero__stat-card--unicorn .hero__stat-row--unicorn {
  justify-content: flex-start;
}
.hero__unicorn-num {
  font-size: 36px !important;
}
.hero__unicorn-num img {
  width: 28px;
  height: auto;
  margin-left: 2px;
}
.hero__stat-source--logos {
  flex-direction: column;
  gap: 8px;
}
.hero__stat-source--logos img {
  display: block;
  height: 18px;
  width: auto;
  object-fit: contain;
}

/* ========== TABLET ========== */
@media (max-width: 1024px) {
  .hero__title {
    font-size: 42px;
  }
  .hero__grid {
    grid-template-columns: 1fr;
  }
  .hero__stats {
    grid-template-columns: repeat(2, 1fr);
  }
  .hero__badge {
    grid-column: span 2;
    justify-self: center;
  }
  .hero__badge img {
    max-width: 120px;
  }
  .hero__stat strong {
    font-size: 26px;
  }
}

/* ========== MOBILE ========== */
@media (max-width: 640px) {
  .hero {
    padding: 32px 0 0;
  }

  .hero__title {
    font-size: 28px;
    margin-bottom: 24px;
  }

  .hero__media {
    min-height: 200px;
  }
  .hero__video {
    min-height: 200px;
  }

  .hero__card {
    padding: 16px;
  }
  .hero__card-preview {
    height: 180px;
  }
  .hero__card-text {
    font-size: 18px;
  }
  .hero__countdown-item strong {
    font-size: 28px;
  }
  .hero__countdown-item span {
    font-size: 14px;
  }

  .hero__stats {
    grid-template-columns: 1fr;
    gap: 12px;
    padding: 14px;
  }

  .hero__badge {
    grid-column: auto;
    order: -1; /* badge yuqorida */
  }
  .hero__badge img {
    max-width: 100px;
  }

  .hero__stat-card {
    min-height: 0;
    padding: 16px 14px 48px; /* source uchun pastki joy */
  }

  .hero__stat-year {
    font-size: 13px;
    padding: 4px 12px;
  }

  .hero__stat-row {
    flex-direction: column;
    gap: 14px;
  }

  .hero__stat-row .hero__stat + .hero__stat {
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    padding-top: 14px;
  }

  .hero__stat strong {
    font-size: 26px;
  }

  .hero__stat span {
    font-size: 13px;
    max-width: 100%;
  }

  /* Unicorn card mobil */
  .hero__stat-card--unicorn {
    padding-bottom: 56px;
  }
  .hero__unicorn-num {
    font-size: 34px !important;
  }
  .hero__unicorn-num img {
    width: 26px;
  }
  .hero__stat-source--logos {
    flex-direction: row;          /* mobilada yonma-yon */
    align-items: center;
    gap: 12px;
    right: 12px;
    bottom: 12px;
  }
  .hero__stat-source--logos img {
    height: 16px;
  }
}
</style>