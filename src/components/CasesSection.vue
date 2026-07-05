<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    id: 1,
    title: 'Никакой абонентской платы',
    description: 'В отличие от конструкторов сайтов (Tilda, Shopify) или готовых CRM-систем, где нужно платить каждый месяц, вы получаете полностью независимый продукт. Вы платите один раз за разработку — и сайт или система навсегда остаются вашей собственностью без скрытых платежей.',
    tags: ['Экономия бюджета', '100% владение'],
   
  },
  {
    id: 2,
    title: 'Абсолютная скорость и независимость от санкций',
    description: 'Сайты создаются на чистом коде с использованием современных технологий (Vue.js и Python). Это гарантирует, что страницы загружаются моментально на любых устройств, а ваш бизнес не зависит от блокировок зарубежных платформ и конструкторов.',
    tags: ['Высокая скорость', 'Надежная архитектура'],
  },
  {
    id: 3,
    title: 'Интеграция с WhatsApp и мессенджерами',
    description: 'Вам не нужно учиться сложным программам. Все уведомления о новых клиентах, записях или бронированиях будут мгновенно приходить вам или вашим менеджерам в Telegram или WhatsApp. Управляйте бизнесом прямо с телефона.',
    tags: ['Всегда под рукой', 'Мгновенный отклик']
  }
])
</script>

<template>
  <section id="portfolio" class="portfolio-section">
    <div class="container">
      <h3 class="section-title">Преимущества</h3>
      <div class="projects-grid">
        <div class="project-card" v-for="project in projects" :key="project.id">
          <div class="project-info">
            <h4>{{ project.title }}</h4>
            <p>{{ project.description }}</p>
            <div class="tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.portfolio-section { padding: 6rem 0; background-color: var(--bg-color); }
.projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 2rem; }
.project-card { background: var(--surface-color); border-radius: 12px; overflow: hidden; border: 1px solid rgba(255,255,255,0.02); transition: all 0.3s ease; }
.project-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px rgba(0,0,0,0.6); border-color: rgba(16, 185, 129, 0.2); }

.project-info { padding: 1.5rem; }
.project-info h4 { font-size: 1.35rem; margin-bottom: 0.7rem; font-weight: 600; }
.project-info p { color: var(--text-muted); font-size: 0.95rem; margin-bottom: 1.5rem; }

.tags { display: flex; flex-wrap: wrap; gap: 0.5rem; }
.tag { background: rgba(255,255,255,0.04); color: var(--text-muted); padding: 4px 10px; border-radius: 4px; font-size: 0.75rem; border: 1px solid rgba(255,255,255,0.02); }

@media (max-width: 768px) {
  .projects-grid { display: flex; flex-wrap: nowrap; overflow-x: auto; gap: 1.5rem; padding-bottom: 2rem; scroll-snap-type: x mandatory; -webkit-overflow-scrolling: touch; scrollbar-width: none; }
  .projects-grid::-webkit-scrollbar { display: none; }
  .project-card { min-width: 85vw; scroll-snap-align: center; transform: none !important; }
}
</style>