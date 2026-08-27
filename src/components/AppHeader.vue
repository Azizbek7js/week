<script setup>
import { ref } from 'vue'
import logo from '../assets/images/logo.svg'

const links = ['Home', 'Program', 'Partners', 'Incentives']
const menuOpen = ref(false)
const langOpen = ref(false)
const lang = ref('English')

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}
function toggleLang() {
  langOpen.value = !langOpen.value
}
function selectLang(value) {
  lang.value = value
  langOpen.value = false
}

function scrollToRegister() {
  document.getElementById('register')?.scrollIntoView({ behavior: 'smooth' })
  menuOpen.value = false
}
</script>

<template>
  <header class="header">
    <div class="container header__bar">
      <a href="#top" class="header__logo" aria-label="ICT Week home">
        <img
            :src="logo"
            alt="ICT Week logo"
            width="67"
            height="42"
            fetchpriority="high"
            decoding="async"
        />
      </a>

      <nav class="header__nav" :class="{ 'is-open': menuOpen }" aria-label="Primary">
        <a
            v-for="link in links"
            :key="link"
            href="#"
            class="header__link"
            :class="{ 'is-active': link === 'Home' }"
            @click="menuOpen = false"
        >
          {{ link }}
        </a>

        <div class="header__mobile-actions">
          <div class="header__lang">
            <button type="button" class="header__lang-btn" @click="toggleLang">
              {{ lang }}
              <svg width="10" height="6" viewBox="0 0 10 6" fill="none" aria-hidden="true">
                <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
              </svg>
            </button>
            <ul v-if="langOpen" class="header__lang-menu">
              <li><button type="button" @click="selectLang('English')">English</button></li>
              <li><button type="button" @click="selectLang('O\'zbek')">O'zbek</button></li>
              <li><button type="button" @click="selectLang('Русский')">Русский</button></li>
            </ul>
          </div>
          <button type="button" class="btn btn-primary" @click="scrollToRegister">Register now</button>
        </div>
      </nav>

      <div class="header__desktop-actions">
        <div class="header__lang">
          <button type="button" class="header__lang-btn" @click="toggleLang" :aria-expanded="langOpen">
            {{ lang }}
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" aria-hidden="true">
              <path d="M1 1l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
            </svg>
          </button>
          <ul v-if="langOpen" class="header__lang-menu">
            <li><button type="button" @click="selectLang('English')">English</button></li>
            <li><button type="button" @click="selectLang('O\'zbek')">O'zbek</button></li>
            <li><button type="button" @click="selectLang('Русский')">Русский</button></li>
          </ul>
        </div>
        <button type="button" class="btn btn-primary" @click="scrollToRegister">Register now</button>
      </div>

      <button type="button" class="header__burger" @click="toggleMenu" :aria-expanded="menuOpen" aria-label="Toggle menu">
        <span></span><span></span><span></span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 50;
  padding: 20px 0;
  contain: layout paint style;
}

.header__bar {
  width: 80%;
  margin-inline: auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding: 8px 8px 8px 24px;
  background: rgb(255 255 255 / 5%);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid var(--border);
  border-radius: 999px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
}

.header__logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: var(--text);
  flex-shrink: 0;
}

.header__nav {
  display: flex;
  align-items: center;
  gap: 4px;
}

.header__link {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  color: var(--text-dim);
  font-size: 14px;
  font-weight: 500;
  padding: 10px 18px;
  border-radius: 999px;
  transition: color 0.15s ease, background 0.15s ease;
  white-space: nowrap;
}
.header__link:hover {
  color: var(--text);
  background: rgba(255, 255, 255, 0.06);
}

/* Figma spec: radius 130px, border 0.94px, padding 16/24/16/24,
   dark base fill (#01141A) with a soft mint radial glow, mint gradient border. */
.header__link.is-active {
  padding: 16px 24px;
  border-radius: 130px;
  border: 0.94px solid transparent;
  background:
      radial-gradient(120% 140% at 50% -20%, rgba(132, 255, 193, 0.18), rgba(132, 255, 193, 0) 65%),
      #01141a;
  background-clip: padding-box;
  color: #ffffff;
  font-weight: 600;
}
.header__link.is-active::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}

.header__desktop-actions {
  display: flex;
  align-items: center;
  gap: 10px;
}

.header__mobile-actions {
  display: none;
}

.header__lang {
  position: relative;
}
.header__lang-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 999px;
  color: var(--text-dim);
  font-size: 14px;
  cursor: pointer;
  padding: 9px 16px;
  transition: border-color 0.15s ease, color 0.15s ease;
}
.header__lang-btn:hover {
  color: var(--text);
  border-color: rgba(255, 255, 255, 0.3);
}
.header__lang-menu {
  position: absolute;
  right: 0;
  top: calc(100% + 6px);
  background: var(--panel);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  list-style: none;
  margin: 0;
  padding: 6px;
  min-width: 130px;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
  z-index: 60;
}
.header__lang-menu button {
  width: 100%;
  text-align: left;
  background: transparent;
  border: none;
  color: var(--text-dim);
  padding: 8px 10px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
}
.header__lang-menu button:hover {
  background: rgba(255, 255, 255, 0.06);
  color: var(--text);
}

.header__burger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  width: 34px;
  height: 34px;
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 8px;
  cursor: pointer;
  flex-shrink: 0;
}
.header__burger span {
  display: block;
  height: 2px;
  width: 16px;
  margin: 0 auto;
  background: var(--text);
}

@media (max-width: 900px) {
  .header__bar {
    width: 100%;
    padding: 8px 8px 8px 16px;
  }
  .header__desktop-actions {
    display: none;
  }
  .header__burger {
    display: flex;
  }
  .header__nav {
    position: fixed;
    inset: 78px 12px auto 12px;
    flex-direction: column;
    align-items: stretch;
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius-md);
    padding: 14px;
    transform: translateY(-12px);
    opacity: 0;
    pointer-events: none;
    transition: transform 0.2s ease, opacity 0.2s ease;
  }
  .header__nav.is-open {
    will-change: transform, opacity;
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }
  .header__link {
    padding: 12px 14px;
  }
  .header__mobile-actions {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    margin-top: 8px;
    padding-top: 10px;
    border-top: 1px solid var(--border);
  }
}
</style>