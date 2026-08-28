<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import heroVideo from '../assets/images/video.mp4'
import photo1 from '../assets/images/photo-1.jpg'
import photo2 from '../assets/images/photo-2.png'
import photo3 from '../assets/images/photo-3.png'
import StartupBlink from '../assets/images/StartupBlink.svg'
import Vector from '../assets/images/Vector.svg'
import Uzum from '../assets/images/uzum.svg'
import TbcBank from '../assets/images/tbc.svg'

const EVENT_DATE = new Date('2026-10-01T00:00:00Z') // UTC time
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

// Pause the interval while the tab is hidden — saves CPU/battery on
// background tabs, and re-syncs the numbers the instant it's visible again.
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
              <img
                  :src="photo3"
                  alt="ICT Week 2026 medal"
                  width="92"
                  height="22"
                  decoding="async"
              />
          </span>
        </div>

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
             <img
                 :src="StartupBlink"
                 alt="ICT Week 2026 medal"
                 width="92"
                 height="22"
                 decoding="async"
             />
          </span>
        </div>

        <div class="hero__stat-card">
          <span class="hero__stat-year">2026</span>
          <div class="hero__stat-row">
            <div class="hero__stat">
              <strong>2
                <img
                    :src="Vector"
                    alt="ICT Week 2026 medal"
                    width="30"
                    height="32"
                    decoding="async"
                />
              </strong>
              <span>Fintech Unicorns</span>
            </div>
          </div>
          <span class="hero__stat-source">
            <img
                :src="Uzum"
                alt="ICT Week 2026 medal"
                width="90"
                height="23"
                style="margin-bottom: 10px"
                decoding="async"
            />
            <img
                :src="TbcBank"
                alt="ICT Week 2026 medal"
                width="90"
                height="23"
                decoding="async"
            />
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
/* Match the reference: outline button carries a soft mint border here,
   not the neutral global border */
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
  font-style: normal;
  font-size: 18px;
  font-weight: 500;
  letter-spacing: 0;
  color: var(--accent-2);
}

.hero__stats {
  margin-top: 20px;
  display: grid;
  grid-template-columns: auto repeat(3, 1fr);
  gap: 14px;
  align-items: center;
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

/* Each stat group is its own bordered card: mint→teal gradient ring,
   rounded corners, "2026" tag pinned top-right, source pinned bottom-right.
   The gradient border is done via the two-background-layers trick, since
   `border` cannot take a gradient value directly (that was the bug). */
.hero__stat-card {
  height: 85%;
  position: relative;
  border: 1.2px solid transparent;
  border-radius: var(--radius-md);
  /* padding-box fill must be near-opaque, or the vivid border-box gradient
     shows through the semi-transparent interior — that was the bug: the
     whole card looked tinted green instead of just a thin border ring. */
  background:
      linear-gradient(180deg, rgba(11, 16, 24, 0.96) 0%, rgba(11, 16, 24, 0.9) 100%) padding-box,
      linear-gradient(270deg, rgba(21, 91, 127, 1) 0%, rgba(27, 219, 134, 1) 100%) border-box;
  padding: 12px 15px 11px;
  overflow: hidden;
}
.hero__stat-year {
  position: absolute;
  top: 0;
  right: 0;
  background: rgba(132, 255, 193, 1);
  color: rgba(18, 27, 38);
  font-size: 15.75px;
  font-weight: 700;
  padding: 5px 16px;
  border-bottom-left-radius: var(--radius-sm);
}
.hero__stat-row {
  display: flex;
  align-items: center;
  gap: 20px;
}
.hero__stat {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 4px;
}
.hero__stat-row .hero__stat + .hero__stat {
  padding-left: 16px;
}
.hero__stat strong {
  display: flex;
  align-items: center;
  gap: 6px;
  font-family: Manrope, sans-serif;
  font-weight: 700;
  font-size: 32px;
  color: #ffffff;
}
.hero__stat span {
  font-family: Manrope , sans-serif;
  max-width: 100px;
  font-weight: 500;
  font-style: Medium;
  font-size: 12px;
  line-height: 126%;
  letter-spacing: 0%;

}
.hero__stat-source {
  position: absolute;
  right: 14px;
  bottom: 10px;
  font-size: 11px;
  color: var(--text-faint);
}

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
    width: auto;
  }
}

@media (max-width: 640px) {
  .hero__title {
    font-size: 30px;
  }
  .hero__stats {
    grid-template-columns: 1fr;
  }
  .hero__badge {
    grid-column: auto;
  }
  .hero__media {
    min-height: 220px;
  }
  .hero__stat-row {
    flex-direction: column;
    gap: 12px;
  }
  .hero__stat-row .hero__stat + .hero__stat {
    border-left: none;
    padding-left: 0;
    border-top: 1px solid var(--border);
    padding-top: 12px;
  }
}
</style>