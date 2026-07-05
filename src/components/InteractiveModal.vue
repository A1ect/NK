<script setup>
defineProps({
  isOpen: {
    type: Boolean,
    default: false
  },
  templateType: {
    type: String,
    default: ''
  }
})

defineEmits(['close'])
</script>

<template>
  <div class="modal-overlay" :class="{ 'active': isOpen }" @click.self="$emit('close')">
    <div class="modal-content">
      
      <div class="modal-header">
        <h3>Абстрактная схема проекта</h3>
        <button class="close-btn" @click="$emit('close')">✕</button>
      </div>

      <div class="modal-body">
        
        <div v-if="templateType === 'landing'" class="skeleton-browser">
          <div class="browser-header"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
          <div class="browser-viewport">
            
            <div class="sk-header">
              <div class="sk-logo sk-anim"></div>
              <div class="sk-nav-links">
                <div class="sk-link sk-anim"></div><div class="sk-link sk-anim"></div><div class="sk-link sk-anim"></div>
              </div>
            </div>

            <div class="sk-hero-split">
              <div class="sk-hero-text">
                <div class="sk-title sk-anim"></div>
                <div class="sk-title short sk-anim"></div>
                <div class="sk-subtitle sk-anim"></div>
                <div class="sk-subtitle short sk-anim"></div>
                <div class="sk-btn sk-anim-accent"></div>
              </div>
              <div class="sk-hero-image sk-anim"></div>
            </div>

            <div class="sk-features-grid">
              <div class="sk-feature-card sk-anim" v-for="i in 3" :key="i">
                <div class="sk-icon sk-anim"></div>
                <div class="sk-line sk-anim"></div>
                <div class="sk-line short sk-anim"></div>
              </div>
            </div>
            
          </div>
        </div>

        <div v-if="templateType === 'corporate'" class="skeleton-browser">
          <div class="browser-header"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
          <div class="browser-viewport">
            
            <div class="sk-header">
              <div class="sk-logo sk-anim"></div>
              <div class="sk-search sk-anim"></div>
            </div>

            <div class="sk-banner sk-anim"></div>

            <div class="sk-corp-layout">
              <div class="sk-sidebar sk-anim">
                <div class="sk-menu-item sk-anim" v-for="i in 4" :key="i"></div>
              </div>
              
              <div class="sk-main-content">
                <div class="sk-title sk-anim" style="width: 50%;"></div>
                <div class="sk-text-block">
                  <div class="sk-line sk-anim" v-for="i in 3" :key="i"></div>
                </div>
                
                <div class="sk-gallery">
                  <div class="sk-gallery-item sk-anim" v-for="i in 4" :key="i"></div>
                </div>
              </div>
            </div>

          </div>
        </div>

        <div v-if="templateType === 'crm'" class="skeleton-browser">
          <div class="browser-header"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
          
          <div class="sk-crm-layout">
            <div class="sk-crm-sidebar">
              <div class="sk-avatar sk-anim"></div>
              <div class="sk-divider"></div>
              <div class="sk-menu-icon sk-anim" v-for="i in 5" :key="i"></div>
            </div>

            <div class="sk-crm-body">
              <div class="sk-crm-header">
                <div class="sk-title sk-anim" style="width: 150px; margin: 0;"></div>
                <div class="sk-avatar small sk-anim"></div>
              </div>
              
              <div class="sk-stats-row">
                <div class="sk-stat-card sk-anim" v-for="i in 3" :key="i"></div>
              </div>
              
              <div class="sk-crm-content-split">
                <div class="sk-chart-box sk-anim">
                  <div class="sk-chart-bar" style="height: 40%"></div>
                  <div class="sk-chart-bar" style="height: 70%"></div>
                  <div class="sk-chart-bar" style="height: 50%"></div>
                  <div class="sk-chart-bar" style="height: 90%"></div>
                  <div class="sk-chart-bar" style="height: 30%"></div>
                </div>
                <div class="sk-table-box sk-anim">
                  <div class="sk-table-row sk-anim" v-for="i in 4" :key="i"></div>
                </div>
              </div>
            </div>
          </div>

        </div>

      </div>
    </div>
  </div>
</template>

<style scoped>
/* --- БАЗОВЫЕ СТИЛИ МОДАЛКИ --- */
.modal-overlay {
  position: fixed; inset: 0; background: rgba(0, 0, 0, 0.85); backdrop-filter: blur(8px);
  display: flex; align-items: center; justify-content: center;
  z-index: 9999; opacity: 0; pointer-events: none; transition: opacity 0.3s ease;
}
.modal-overlay.active { opacity: 1; pointer-events: all; }
.modal-content {
  background: var(--surface-color); width: 95%; max-width: 900px; border-radius: 12px;
  border: 1px solid rgba(16, 185, 129, 0.3); overflow: hidden; transform: translateY(20px); transition: transform 0.3s ease;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
}
.modal-overlay.active .modal-content { transform: translateY(0); }
.modal-header { padding: 1.2rem 1.5rem; display: flex; justify-content: space-between; align-items: center; background: #16161e; border-bottom: 1px solid rgba(255,255,255,0.05); }
.modal-header h3 { margin: 0; font-size: 1.1rem; color: #f3f4f6; }
.close-btn { background: none; border: none; color: #9ca3af; font-size: 1.5rem; cursor: pointer; transition: color 0.2s; padding: 0; line-height: 1; }
.close-btn:hover { color: #ef4444; }
.modal-body { padding: 2rem; background: #0a0a0f; display: flex; justify-content: center; }

/* --- ОКНО БРАУЗЕРА --- */
.skeleton-browser {
  background: #1a1b26; border-radius: 8px; border: 1px solid #292e42;
  width: 100%; height: 480px; display: flex; flex-direction: column; overflow: hidden;
}
.browser-header { background: #16161e; padding: 12px 15px; display: flex; gap: 8px; border-bottom: 1px solid #292e42; }
.dot { width: 12px; height: 12px; border-radius: 50%; }
.dot.red { background: #f7768e; } .dot.yellow { background: #e0af68; } .dot.green { background: #9ece6a; }
.browser-viewport { flex: 1; padding: 20px; display: flex; flex-direction: column; gap: 20px; overflow-y: auto; }

/* --- АНИМАЦИЯ ПЕРЕЛИВАНИЯ (SHIMMER) --- */
@keyframes shimmer {
  0% { background-position: -400px 0; }
  100% { background-position: 400px 0; }
}
.sk-anim {
  background: linear-gradient(90deg, #24283b 25%, #2f354d 50%, #24283b 75%);
  background-size: 800px 100%;
  animation: shimmer 2s infinite linear;
  border-radius: 6px;
}
.sk-anim-accent {
  background: linear-gradient(90deg, rgba(16,185,129,0.3) 25%, rgba(16,185,129,0.6) 50%, rgba(16,185,129,0.3) 75%);
  background-size: 800px 100%;
  animation: shimmer 2s infinite linear;
  border-radius: 6px;
}

/* --- ОБЩИЕ ЭЛЕМЕНТЫ СКЕЛЕТА --- */
.sk-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
.sk-logo { width: 100px; height: 24px; }
.sk-nav-links { display: flex; gap: 15px; }
.sk-link { width: 50px; height: 12px; }
.sk-title { width: 80%; height: 28px; margin-bottom: 10px; }
.sk-title.short { width: 50%; }
.sk-subtitle { width: 90%; height: 14px; margin-bottom: 8px; opacity: 0.6; }
.sk-subtitle.short { width: 60%; margin-bottom: 20px; }
.sk-btn { width: 140px; height: 40px; border-radius: 20px; }
.sk-line { width: 100%; height: 10px; margin-bottom: 8px; opacity: 0.6; }
.sk-line.short { width: 70%; }

/* --- 1. ЛЕНДИНГ --- */
.sk-hero-split { display: flex; gap: 30px; align-items: center; margin-bottom: 30px; }
.sk-hero-text { flex: 1; }
.sk-hero-image { flex: 1; height: 200px; border-radius: 12px; }
.sk-features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
.sk-feature-card { padding: 15px; border-radius: 12px; display: flex; flex-direction: column; align-items: center; background: #1f2335; }
.sk-icon { width: 40px; height: 40px; border-radius: 50%; margin-bottom: 15px; }

/* --- 2. КОРПОРАТИВНЫЙ САЙТ --- */
.sk-search { width: 150px; height: 24px; border-radius: 12px; }
.sk-banner { width: 100%; height: 120px; border-radius: 12px; margin-bottom: 20px; }
.sk-corp-layout { display: flex; gap: 20px; }
.sk-sidebar { width: 200px; display: flex; flex-direction: column; gap: 10px; padding: 15px; background: #1f2335; border-radius: 12px; height: 200px; }
.sk-menu-item { width: 100%; height: 16px; opacity: 0.8; }
.sk-main-content { flex: 1; }
.sk-text-block { margin-bottom: 20px; }
.sk-gallery { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; }
.sk-gallery-item { height: 100px; border-radius: 8px; }

/* --- 3. CRM ПАНЕЛЬ --- */
.sk-crm-layout { display: flex; height: calc(100% - 41px); }
.sk-crm-sidebar { width: 70px; background: #16161e; border-right: 1px solid #292e42; display: flex; flex-direction: column; align-items: center; padding: 20px 0; gap: 20px; }
.sk-avatar { width: 36px; height: 36px; border-radius: 50%; }
.sk-avatar.small { width: 28px; height: 28px; }
.sk-divider { width: 30px; height: 2px; background: #292e42; }
.sk-menu-icon { width: 24px; height: 24px; border-radius: 6px; opacity: 0.7; }
.sk-crm-body { flex: 1; padding: 20px; display: flex; flex-direction: column; gap: 20px; background: #1a1b26; }
.sk-crm-header { display: flex; justify-content: space-between; align-items: center; padding-bottom: 15px; border-bottom: 1px solid #292e42; }
.sk-stats-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; }
.sk-stat-card { height: 80px; background: #1f2335; border-radius: 10px; border: 1px solid #292e42; }
.sk-crm-content-split { display: flex; gap: 15px; flex: 1; }
.sk-chart-box { flex: 1; background: #1f2335; border-radius: 10px; border: 1px solid #292e42; display: flex; align-items: flex-end; justify-content: space-around; padding: 15px; }
.sk-chart-bar { width: 12%; background: rgba(16,185,129,0.5); border-radius: 4px 4px 0 0; }
.sk-table-box { flex: 1.5; background: #1f2335; border-radius: 10px; padding: 15px; display: flex; flex-direction: column; gap: 10px; border: 1px solid #292e42; }
.sk-table-row { width: 100%; height: 24px; opacity: 0.5; }

/* Адаптивность для модалки на телефонах */
@media (max-width: 768px) {
  .sk-hero-split { flex-direction: column; }
  .sk-corp-layout { flex-direction: column; }
  .sk-sidebar { width: 100%; height: auto; }
  .sk-crm-content-split { flex-direction: column; }
  .sk-features-grid { grid-template-columns: 1fr; }
  .sk-stats-row { grid-template-columns: 1fr; }
}
</style>