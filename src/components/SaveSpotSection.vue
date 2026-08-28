<script setup>
import saveSpotJpg from '../assets/images/photo-4.jpg'

function scrollToRegister() {
  document.getElementById('register')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section class="section save">
    <div class="container">
      <div class="save__card">
        <div class="save__text">
          <h2>Save your spot today!</h2>
          <p>
            Every unicorn starts as a single star.
            <br />
            Together they become the Northern Lights.
          </p>
          <p>
            Welcome to Uzbekistan, where visionary government support and a thriving
            innovation ecosystem help founders turn bold ideas into global ventures.
          </p>
          <p>
            Here, startups and tech companies don't just become part of the Northern
            Lights—they discover their North Star and follow it all the way to
            international success.
          </p>
          <button type="button" class="btn btn-primary" @click="scrollToRegister">
            Register now
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" aria-hidden="true">
              <path d="M2 10L10 2M10 2H4M10 2v6" stroke="#062015" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </button>
        </div>

        <picture class="save__media">
          <img
              :src="saveSpotJpg"
              alt="Speaker presenting on stage at ICT Week"
              width="386"
              height="281"
              loading="lazy"
              decoding="async"
          />
        </picture>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Values below are taken directly from Figma's Inspect panel for this frame:
   Width: Fill (1280px) · Height: Hug (484px) · Radius: 24px
   Padding: 36 top / 36 right / 36 bottom / 42 left · Gap: 32px
   Background: #121B26 @ 40% opacity */
.save__card {
  background: #121B2666;
  border: 1px solid var(--border-strong);
  border-radius: 24px;
  padding: 36px 36px 36px 42px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
  align-items: center;
}
.save__text h2 {
  font-family: 'Manrope', var(--font);
  font-weight: 700;
  font-size: 48px;
  line-height: 1.2;
  letter-spacing: 0;
  color: #ededf2;
  margin: 0 0 16px;
}
.save__text p {
  font-family: 'Manrope', var(--font);
  font-weight: 500;
  font-size: 18px;
  line-height: 1.6;
  letter-spacing: 0;
  color: var(--text-dim);
  margin: 0 0 14px;
}
.save__media {
  display: block;
  border-radius: var(--radius-md);
  overflow: hidden;
  aspect-ratio: 386 / 281;
  border: 1px solid var(--border);
}
.save__media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

@media (max-width: 1024px) {
  .save__card {
    padding: 26px 26px 26px 30px;
    gap: 24px;
  }
  .save__text h2 {
    font-size: 36px;
  }
}

@media (max-width: 768px) {
  .save__card {
    grid-template-columns: 1fr;
  }
  .save__media {
    order: -1;
  }
}

@media (max-width: 640px) {
  .save__card {
    padding: 20px;
    border-radius: var(--radius-md);
  }
  .save__text h2 {
    font-size: 28px;
  }
  .save__text p {
    font-size: 15px;
  }
}
</style>