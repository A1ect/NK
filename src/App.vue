<script setup>
import { ref } from 'vue'

// Импортируем компоненты
import HeroSection from './components/HeroSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import CasesSection from './components/CasesSection.vue'
import AppFooter from './components/AppFooter.vue'
import InteractiveModal from './components/InteractiveModal.vue'

// Логика навигации
const navLinksLeft = ref([
  { name: 'Миссия', target: '#mission' },
  { name: 'Услуги', target: '#services' }
])
const navLinksRight = ref([
  { name: 'Преимущества', target: '#portfolio' },
  { name: 'Контакты', target: '#contact' }
])

const isMobileMenuOpen = ref(false)
const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
  document.body.style.overflow = isMobileMenuOpen.value ? 'hidden' : 'auto'
}

const scrollToSection = (targetId) => {
  const element = document.querySelector(targetId)
  if (element) element.scrollIntoView({ behavior: 'smooth' })
}

const mobileScrollTo = (targetId) => {
  toggleMobileMenu()
  setTimeout(() => scrollToSection(targetId), 300)
}

// Логика модального окна для скелетов
const isModalOpen = ref(false)
const selectedTemplate = ref('')

const openSkeletonModal = (type) => {
  selectedTemplate.value = type
  isModalOpen.value = true
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  isModalOpen.value = false
  document.body.style.overflow = 'auto'
}
</script>

<template>
  <div class="portfolio-layout">
    
    <nav class="custom-navbar">
      <div class="nav-container">
        <div class="nav-group nav-right desktop-only">
          <a v-for="link in navLinksLeft" :key="link.name" @click.prevent="scrollToSection(link.target)" href="#">{{ link.name }}</a>
        </div>
        <div class="nav-center-circle" @click="scrollToSection('.hero-section')" title="В начало">
          <div class="inner-circle"></div>
        </div>
        <div class="nav-group nav-left desktop-only">
          <a v-for="link in navLinksRight" :key="link.name" @click.prevent="scrollToSection(link.target)" href="#">{{ link.name }}</a>
        </div>
        <button class="mobile-menu-btn" :class="{ 'active': isMobileMenuOpen }" @click="toggleMobileMenu">
          <span></span><span></span><span></span>
        </button>
      </div>
    </nav>
    <div class="mobile-menu-overlay" :class="{ 'open': isMobileMenuOpen }">
        <div class="mobile-nav-links">
          <a v-for="link in navLinksLeft" :key="link.name" @click.prevent="mobileScrollTo(link.target)" href="#">{{ link.name }}</a>
          <a v-for="link in navLinksRight" :key="link.name" @click.prevent="mobileScrollTo(link.target)" href="#">{{ link.name }}</a>
        </div>
      </div>

    <HeroSection />
    
    <ServicesSection @open-modal="openSkeletonModal" />
    
    <CasesSection />
    <AppFooter />

    <InteractiveModal :is-open="isModalOpen" :template-type="selectedTemplate" @close="closeModal" />

  </div>
</template>

<style>
/* --- ГЛОБАЛЬНЫЕ СТИЛИ --- */
html, body {
  margin: 0; padding: 0; width: 100%; overflow-x: hidden; background-color: #08080a;
}
*, *::before, *::after { box-sizing: border-box; }

:root {
  --bg-color: #08080a; --surface-color: #111115; --accent-color: #10b981; 
  --accent-glow: rgba(16, 185, 129, 0.2); --text-main: #f3f4f6; --text-muted: #9ca3af;
}

.portfolio-layout { background-color: var(--bg-color); color: var(--text-main); line-height: 1.6; font-family: 'Inter', sans-serif; }
.container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
.section-title { font-size: 2rem; margin-bottom: 2.5rem; color: var(--text-main); border-left: 4px solid var(--accent-color); padding-left: 1rem; font-weight: 700; }

/* --- СТИЛИ НАВИГАЦИИ --- */
.custom-navbar { position: fixed; top: 0; left: 0; width: 100%; height: 70px; background: rgba(8, 8, 10, 0.8); backdrop-filter: blur(12px); border-bottom: 1px solid rgba(255, 255, 255, 0.05); z-index: 1000; display: flex; align-items: center; }
.nav-container { width: 100%; max-width: 1200px; margin: 0 auto; padding: 0 20px; display: flex; justify-content: space-between; align-items: center; position: relative; }
.nav-group { display: flex; gap: 3rem; width: 40%; }
.nav-right { justify-content: flex-end; }
.nav-group a { color: var(--text-muted); text-decoration: none; font-weight: 500; font-size: 1rem; transition: color 0.3s ease; }
.nav-group a:hover { color: var(--accent-color); }

.nav-center-circle { width: 50px; height: 50px; border-radius: 50%; border: 2px solid rgba(16, 185, 129, 0.4); display: flex; align-items: center; justify-content: center; cursor: pointer; transition: all 0.4s; background: var(--surface-color); position: absolute; left: 50%; transform: translateX(-50%); z-index: 1001; }
.inner-circle { width: 14px; height: 14px; border-radius: 50%; background: var(--accent-color); transition: transform 0.3s ease; }
.nav-center-circle:hover { transform: translateX(-50%) scale(1.1); border-color: var(--accent-color); box-shadow: 0 0 15px rgba(16, 185, 129, 0.4); }
.nav-center-circle:hover .inner-circle { transform: scale(1.3); }

/* Мобильное меню */
.mobile-menu-btn { display: none; background: none; border: none; cursor: pointer; width: 30px; height: 20px; position: relative; z-index: 1001; }
.mobile-menu-btn span { display: block; width: 100%; height: 2px; background-color: var(--text-main); position: absolute; transition: all 0.3s; }
.mobile-menu-btn span:nth-child(1) { top: 0; } .mobile-menu-btn span:nth-child(2) { top: 9px; } .mobile-menu-btn span:nth-child(3) { top: 18px; }
.mobile-menu-btn.active span:nth-child(1) { transform: rotate(45deg); top: 9px; background-color: var(--accent-color); }
.mobile-menu-btn.active span:nth-child(2) { opacity: 0; }
.mobile-menu-btn.active span:nth-child(3) { transform: rotate(-45deg); top: 9px; background-color: var(--accent-color); }

.mobile-menu-overlay { position: fixed; inset: 0; background: rgba(8, 8, 10, 0.98); backdrop-filter: blur(15px); display: flex; align-items: center; justify-content: center; opacity: 0; pointer-events: none; transition: opacity 0.4s ease; z-index: 999; }
.mobile-menu-overlay.open { opacity: 1; pointer-events: all; }
.mobile-nav-links { display: flex; flex-direction: column; align-items: center; gap: 2rem; transform: translateY(20px); transition: transform 0.4s; }
.mobile-menu-overlay.open .mobile-nav-links { transform: translateY(0); }
.mobile-nav-links a { font-size: 2rem; color: var(--text-main); text-decoration: none; font-weight: 700; transition: color 0.3s; }
.mobile-nav-links a:hover { color: var(--accent-color); }

@media (max-width: 768px) {
  .desktop-only { display: none; }
  .mobile-menu-btn { display: block; }
  .nav-center-circle { left: 50%; transform: translateX(-50%); } 
}
</style>