<script setup>
import saveSpotPhoto from '../assets/images/logo.svg'

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
        <img
            class="save__media"
            :src="saveSpotPhoto"
            alt="Speaker presenting on stage at ICT Week"
            width="386"
            height="281"
            loading="lazy"
            decoding="async"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.save__card {
  background: linear-gradient(135deg, rgba(20, 38, 30, 0.6), rgba(10, 16, 13, 0.6));
  border: 1px solid var(--border-strong);
  border-radius: var(--radius-lg);
  padding: 44px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}
.save__text h2 {
  font-size: 34px;
  margin: 0 0 16px;
}
.save__text p {
  color: var(--text-dim);
  font-size: 14.5px;
  line-height: 1.6;
  margin: 0 0 14px;
}
.save__media {
  border-radius: var(--radius-md);
  min-height: 260px;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border: 1px solid var(--border);
}

@media (max-width: 1024px) {
  .save__card {
    padding: 30px;
    gap: 26px;
  }
  .save__text h2 {
    font-size: 28px;
  }
}

@media (max-width: 768px) {
  .save__card {
    grid-template-columns: 1fr;
  }
  .save__media {
    order: -1;
    min-height: 200px;
  }
}

@media (max-width: 640px) {
  .save__card {
    padding: 22px;
    border-radius: var(--radius-md);
  }
}
</style>