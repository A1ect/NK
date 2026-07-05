<template>
  <div>
    <header class="hero-section">
      <div class="hero-content">
        <h1 class="hero-title">Цифровые решения для роста бизнеса</h1>
        <h2 class="subtitle">Разработка сайтов & Автоматизация бизнес-процессов</h2>
        <p class="bio">
          Создаю быстрые продающие сайты и кастомные системы автоматизации (CRM, Telegram-боты). Помогаю малому и среднему бизнесу привлекать клиентов, автоматизировать учёт записей и мгновенно получать заявки прямо на смартфон без ежемесячных платежей.
        </p>
        <div class="hero-actions">
          <a href="#services" class="btn-primary">Выбрать решение</a>
          <a href="#contact" class="btn-secondary">Обсудить задачу</a>
        </div>
      </div>
      
      <div class="hero-visual">
        <div class="aurora-container">
          <div class="aurora-blob blob-1"></div>
          <div class="aurora-blob blob-2"></div>
          <div class="aurora-blob blob-3"></div>
        </div>
      </div>
    </header>

    <section id="mission" class="mission-section">
      <div class="container">
        <div class="mission-box">
          <span class="mission-badge">Миссия ИП</span>
          <h3 class="mission-title">Доступная цифровизация и конкурентоспособность МСБ</h3>
          <p class="mission-text">Современный рынок Казахстана диктует жесткие правила: если твоего бизнеса нет в смартфоне клиента — тебя нет на рынке.</p>
          <p class="mission-text"><strong>Моя цель</strong> — сломать этот барьер. Я создаю умные, быстрые и доступные цифровые продукты, которые автоматизируют рутину и повышают эффективность локального бизнеса.</p>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.hero-section { min-height: 100vh; display: flex; align-items: center; position: relative; overflow: hidden; padding-top: 70px; }
.hero-content { position: relative; z-index: 2; max-width: 750px; padding-left: 5%; }
.hero-title { font-size: 4rem; font-weight: 800; line-height: 1.1; margin-bottom: 1rem; letter-spacing: -1px; }
.subtitle { font-size: 1.8rem; color: var(--accent-color); font-weight: 400; margin-bottom: 1.5rem; }
.bio { font-size: 1.15rem; color: var(--text-muted); margin-bottom: 2.5rem; max-width: 600px; }

.hero-actions { display: flex; gap: 1rem; }
.btn-primary, .btn-secondary { padding: 14px 28px; text-decoration: none; font-weight: 600; border-radius: 6px; transition: all 0.3s; }
.btn-primary { background: var(--accent-color); color: var(--bg-color); }
.btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(16, 185, 129, 0.3); }
.btn-secondary { background: transparent; color: var(--text-main); border: 1px solid var(--text-muted); }
.btn-secondary:hover { border-color: var(--text-main); background: rgba(255,255,255,0.03); }

/* Аврора */
.hero-visual { position: absolute; top: 0; right: 0; width: 55%; height: 100%; z-index: 1; overflow: hidden; mask-image: linear-gradient(to right, transparent 0%, black 40%); -webkit-mask-image: linear-gradient(to right, transparent 0%, black 40%); }
.aurora-container { position: absolute; width: 100%; height: 100%; filter: blur(80px); opacity: 0.6; transform: translateZ(0); }
.aurora-blob { position: absolute; border-radius: 50%; animation: aurora-flow 15s infinite alternate ease-in-out; will-change: transform; }
.blob-1 { top: -10%; right: -10%; width: 600px; height: 600px; background: radial-gradient(circle, rgba(16, 185, 129, 0.8) 0%, transparent 70%); animation-delay: 0s; }
.blob-2 { bottom: -10%; right: 20%; width: 500px; height: 500px; background: radial-gradient(circle, rgba(14, 165, 233, 0.6) 0%, transparent 70%); animation-delay: -5s; animation-duration: 20s; }
.blob-3 { top: 30%; right: 40%; width: 450px; height: 450px; background: radial-gradient(circle, rgba(4, 120, 87, 0.9) 0%, transparent 70%); animation-delay: -10s; animation-duration: 18s; }

@keyframes aurora-flow {
  0% { transform: translate(0, 0) scale(1) rotate(0deg); }
  33% { transform: translate(-150px, 100px) scale(1.1) rotate(15deg); }
  66% { transform: translate(100px, -150px) scale(0.9) rotate(-10deg); }
  100% { transform: translate(-50px, 150px) scale(1.2) rotate(20deg); }
}

/* Миссия */
.mission-section { padding: 4rem 0; background: linear-gradient(180deg, var(--bg-color) 0%, var(--surface-color) 100%); }
.mission-box { background: rgba(255, 255, 255, 0.02); border: 1px solid rgba(16, 185, 129, 0.15); padding: 3rem; border-radius: 16px; position: relative; overflow: hidden; }
.mission-badge { background: rgba(16, 185, 129, 0.1); color: var(--accent-color); padding: 6px 14px; border-radius: 30px; font-size: 0.85rem; font-weight: 600; text-transform: uppercase; letter-spacing: 1px; display: inline-block; margin-bottom: 1.5rem; }
.mission-title { font-size: 2.2rem; margin-bottom: 1.5rem; font-weight: 700; }
.mission-text { font-size: 1.1rem; color: var(--text-muted); margin-bottom: 1.2rem; max-width: 900px; }

@media (max-width: 768px) {
  .hero-section { padding-top: 6rem; text-align: center; }
  .hero-content { padding: 0 20px; width: 100%; }
  .hero-title { font-size: 2.2rem; }
  .subtitle { font-size: 1.2rem; margin-bottom: 1rem; }
  .bio { font-size: 1rem; margin-bottom: 2rem; }
  .hero-actions { flex-direction: column; gap: 15px; }
  .hero-visual { width: 100%; mask-image: linear-gradient(to top, transparent 0%, black 70%); -webkit-mask-image: linear-gradient(to top, transparent 0%, black 70%); }
  .aurora-container { opacity: 0.4; }
  .mission-box { padding: 1.5rem; }
  .mission-title { font-size: 1.5rem; }
}
</style>