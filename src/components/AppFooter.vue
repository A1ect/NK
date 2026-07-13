<template>
  <footer id="contact" class="footer-section">
    <div class="container">
      <h2>Давайте создадим что-то крутое</h2>
      <p class="footer-sub">Оказание услуг в сегменте B2B на основании Договора возмездного оказания услуг.</p>
      
      <div class="social-links">
         <a href="https://t.me/kzNK31" 
         class="social-item" 
         target="_blank" 
         rel="noopener noreferrer"
  >
    Telegram
  </a>
        
        
      </div>
      
      <div class="legal-info">
        <p>© 2026 Развитие и поддержка МСБ. Все права защищены.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-section { padding: 5rem 0; background: var(--surface-color); border-top: 1px solid rgba(255,255,255,0.03); }
.footer-section h2 { font-size: 2.2rem; margin-bottom: 0.5rem; font-weight: 700; text-align: center;}
.footer-sub { color: var(--accent-color); text-align: center; font-size: 1.05rem; margin-bottom: 3rem; font-weight: 500; }
.social-links { display: flex; justify-content: center; gap: 1.5rem; margin-bottom: 4rem; }

.social-item { padding: 10px 24px; background: var(--bg-color); color: var(--text-main); text-decoration: none; font-weight: 600; border-radius: 6px; border: 1px solid rgba(255,255,255,0.05); transition: all 0.3s; }
.social-item:hover { color: var(--accent-color); border-color: var(--accent-color); background: rgba(16, 185, 129, 0.02); }
.legal-info { text-align: center; color: #6b7280; font-size: 0.85rem; border-top: 1px solid rgba(255,255,255,0.05); padding-top: 2rem; }

@media (max-width: 768px) {
  .social-links { flex-direction: column; align-items: center; gap: 1rem; }
  .social-item { width: 100%; max-width: 280px; text-align: center; }
}
</style>