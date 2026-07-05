<script setup>
import { ref } from 'vue'

// Определяем события, которые компонент может отправлять родителю
const emit = defineEmits(['open-modal'])

const websiteTypes = ref([
  {
    id: 'landing',
    title: 'Лендинг (Landing Page)',
    idealFor: 'Быстрого запуска продаж конкретного товара, услуги или сбора заявок.',
    result: 'Стильный одностраничный сайт с высокой конверсией, полностью оптимизированный под запуск рекламы.'
  },
  {
    id: 'corporate',
    title: 'Сайт-визитка / Многостраничник',
    idealFor: 'Компаний, которым нужно подробно презентовать себя, свои ценности, команду и прайс-лист.',
    result: 'Презентабельный ресурс из нескольких страниц, который формирует доверие у клиентов и партнеров.'
  },
  {
    id: 'crm',
    title: 'Кастомные CRM и веб-приложения',
    idealFor: 'Автоматизации процессов.',
    result: 'Индивидуальную панель управления и учета, которая автоматизирует рутину и адаптирована под ваши рабочие задачи.'
  }
])
</script>

<template>
  <section id="services" class="services-section">
    <div class="container">
      <h3 class="section-title">Какой сайт нужен вашему бизнесу?</h3>
      
      <div class="services-grid">
        <div class="service-card" v-for="site in websiteTypes" :key="site.id">
          <h4>{{ site.title }}</h4>
          <div class="service-info">
            <p><strong>Идеально для:</strong> {{ site.idealFor }}</p>
            <p><strong>Что вы получаете:</strong> {{ site.result }}</p>
          </div>
          
          <button class="demo-btn" @click="emit('open-modal', site.id)">
            Посмотреть пример верстки
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section { padding: 5rem 0; background-color: var(--bg-color); }
.container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
.section-title { font-size: 2rem; margin-bottom: 2.5rem; border-left: 4px solid var(--accent-color); padding-left: 1rem; }

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.service-card {
  background: var(--surface-color);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.05);
  display: flex;
  flex-direction: column;
}

.service-card h4 {
  color: var(--accent-color);
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
}

.service-info p {
  font-size: 0.95rem;
  color: var(--text-muted);
  margin-bottom: 1rem;
  line-height: 1.5;
}

.service-info strong {
  color: var(--text-main);
}

.demo-btn {
  margin-top: auto;
  padding: 12px;
  background: transparent;
  color: var(--text-main);
  border: 1px solid var(--accent-color);
  border-radius: 6px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s;
}

.demo-btn:hover {
  background: var(--accent-color);
  color: #000;
}

/* --- АДАПТИВНОСТЬ ДЛЯ СМАРТФОНОВ (Горизонтальная карусель) --- */
@media (max-width: 768px) {
  /* ИСПРАВЛЕНО: добавлена 's' в services-grid */
  .services-grid {
    display: flex; 
    flex-wrap: nowrap;
    overflow-x: auto; /* Включаем горизонтальный скролл */
    gap: 1.5rem;
    padding-bottom: 2rem; /* Место под тень карточек */
    
    /* Магнитная доводка к центру */
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch; /* Плавность для iOS */
    scrollbar-width: none; /* Прячем системный скроллбар */
  }

  /* ИСПРАВЛЕНО: добавлена 's' в services-grid */
  .services-grid::-webkit-scrollbar {
    display: none;
  }

  .service-card {
    min-width: 85vw; /* Делаем карточку на 85% ширины экрана */
    scroll-snap-align: center; /* Примагничиваем ровно по центру */
    transform: none !important; /* Отключаем прыжок при наведении пальцем */
  }
}
</style>