<script setup>
import AppHeader from '../components/AppHeader.vue'
import HeroSection from '../components/HeroSection.vue'
import SaveSpotSection from '../components/SaveSpotSection.vue'
import PastAttendees from '../components/PastAttendees.vue'
import EventTabs from '../components/EventTabs.vue'
import ITParkShowcase from '../components/ITParkShowcase.vue'
import PartnersSection from '../components/PartnersSection.vue'
import RegisterForm from '../components/RegisterForm.vue'
import AppFooter from '../components/AppFooter.vue'
</script>

<template>
  <div class="page">
    <AppHeader />
    <main>
      <HeroSection />
      <SaveSpotSection />
      <PastAttendees />
      <EventTabs />
      <ITParkShowcase />
      <PartnersSection />
      <RegisterForm />
    </main>
  </div>
</template>
