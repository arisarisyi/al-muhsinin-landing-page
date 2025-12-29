<script lang="ts">
  export let scrollTo: (id: string) => void;
  export let activeSection: string;

  let mobileMenuOpen = false;
  let scrolled = false;

  const toggleMenu = () => {
    mobileMenuOpen = !mobileMenuOpen;
    document.body.style.overflow = mobileMenuOpen ? 'hidden' : '';
  };

  const closeMenu = () => {
    mobileMenuOpen = false;
    document.body.style.overflow = '';
  };

  const handleScroll = () => {
    scrolled = window.scrollY > 50;
  };

  if (typeof window !== 'undefined') {
    window.addEventListener('scroll', handleScroll);
  }
</script>

<header class:scrolled>
  <div class="container">
    <div class="header-inner">
      <div class="logo">
        <img src='/al-muhsinin.png' alt="Logo Al-Muhsinin" />
        <span>Al-Muhsinin</span>
      </div>

      <nav class={`nav-links ${mobileMenuOpen ? 'open' : ''}`}>
        <a
          href="#home"
          class:active={activeSection === 'home'}
          on:click|preventDefault={() => { scrollTo('home'); closeMenu(); }}
        >
          <span class="nav-text">Beranda</span>
          <span class="nav-indicator"></span>
        </a>
        <a
          href="#about"
          class:active={activeSection === 'about'}
          on:click|preventDefault={() => { scrollTo('about'); closeMenu(); }}
        >
          <span class="nav-text">Tentang</span>
          <span class="nav-indicator"></span>
        </a>
        <a
          href="#activities"
          class:active={activeSection === 'activities'}
          on:click|preventDefault={() => { scrollTo('activities'); closeMenu(); }}
        >
          <span class="nav-text">Kegiatan</span>
          <span class="nav-indicator"></span>
        </a>
        <a
          href="#facilities"
          class:active={activeSection === 'facilities'}
          on:click|preventDefault={() => { scrollTo('facilities'); closeMenu(); }}
        >
          <span class="nav-text">Dokumentasi</span>
          <span class="nav-indicator"></span>
        </a>
        <a
          href="#testimonials"
          class:active={activeSection === 'testimonials'}
          on:click|preventDefault={() => { scrollTo('testimonials'); closeMenu(); }}
        >
          <span class="nav-text">Testimoni</span>
          <span class="nav-indicator"></span>
        </a>
        <a href="#contact" class="btn-cta" on:click|preventDefault={() => { scrollTo('contact'); closeMenu(); }}>
          <span>Kontak</span>
        </a>
      </nav>

      <button
        class="mobile-menu-btn"
        class:open={mobileMenuOpen}
        on:click={toggleMenu}
        on:keydown={(e) => e.key === 'Enter' && toggleMenu()}
        aria-label="Toggle mobile menu"
        aria-expanded={mobileMenuOpen}
      >
        <span class="hamburger"></span>
        <span class="hamburger"></span>
        <span class="hamburger"></span>
      </button>
    </div>
  </div>

  <button
    class="mobile-overlay"
    class:active={mobileMenuOpen}
    on:click={closeMenu}
    aria-label="Close mobile menu"
  ></button>
</header>

<style>
  header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: var(--z-fixed);
    transition: all var(--transition-normal);
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid transparent;
  }

  header.scrolled {
    background: rgba(255, 255, 255, 0.98);
    box-shadow: var(--shadow-md);
    border-bottom-color: var(--gray-100);
  }

  .header-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: var(--space-5) 0;
    transition: padding var(--transition-normal);
  }

  header.scrolled .header-inner {
    padding: var(--space-3) 0;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: var(--space-3);
    font-size: var(--text-xl);
    font-weight: 800;
    color: var(--primary);
    text-decoration: none;
    transition: transform var(--transition-base);
  }

  .logo:hover {
    transform: scale(1.02);
  }

  .logo img {
    height: 45px;
    width: auto;
    object-fit: contain;
  }

  .nav-links {
    display: flex;
    align-items: center;
    gap: var(--space-2);
  }

  .nav-links a {
    position: relative;
    padding: var(--space-2) var(--space-4);
    color: var(--gray-700);
    font-weight: 600;
    font-size: var(--text-sm);
    text-decoration: none;
    transition: color var(--transition-base);
    border-radius: var(--radius-lg);
  }

  .nav-text {
    position: relative;
    z-index: 1;
  }

  .nav-indicator {
    position: absolute;
    bottom: var(--space-1);
    left: 50%;
    transform: translateX(-50%) scaleX(0);
    width: calc(100% - var(--space-4));
    height: 2px;
    background: var(--primary);
    transition: transform var(--transition-normal);
  }

  .nav-links a:hover {
    color: var(--primary);
    background: var(--gray-50);
  }

  .nav-links a:hover .nav-indicator {
    transform: translateX(-50%) scaleX(1);
  }

  .nav-links a.active {
    color: var(--primary);
  }

  .nav-links a.active .nav-indicator {
    transform: translateX(-50%) scaleX(1);
  }

  .btn-cta {
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: var(--white) !important;
    padding: var(--space-3) var(--space-6) !important;
    border-radius: var(--radius-full);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-normal);
  }

  .btn-cta:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-primary);
    background: linear-gradient(135deg, var(--primary-light), var(--primary));
  }

  .btn-cta .nav-indicator {
    display: none;
  }

  .mobile-menu-btn {
    display: none;
    flex-direction: column;
    gap: var(--space-1);
    padding: var(--space-2);
    background: transparent;
    border: none;
    cursor: pointer;
    z-index: calc(var(--z-fixed) + 1);
  }

  .hamburger {
    width: 24px;
    height: 2px;
    background: var(--gray-800);
    border-radius: var(--radius-full);
    transition: all var(--transition-normal);
    transform-origin: center;
  }

  .mobile-menu-btn:hover .hamburger {
    background: var(--primary);
  }

  .mobile-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    opacity: 0;
    transition: opacity var(--transition-normal);
    z-index: calc(var(--z-fixed) - 1);
  }

  @media (max-width: 1024px) {
    .nav-links a {
      padding: var(--space-2) var(--space-3);
      font-size: var(--text-xs);
    }

    .btn-cta {
      padding: var(--space-2) var(--space-4) !important;
      font-size: var(--text-xs) !important;
    }
  }

  @media (max-width: 768px) {
    .header-inner {
      padding: var(--space-4) 0;
    }

    .mobile-menu-btn {
      display: flex;
    }

    .nav-links {
      position: fixed;
      top: 0;
      right: 0;
      width: 80%;
      max-width: 300px;
      height: 100vh;
      background: var(--white);
      flex-direction: column;
      align-items: stretch;
      padding: var(--space-20) var(--space-8) var(--space-8);
      box-shadow: var(--shadow-2xl);
      transform: translateX(100%);
      transition: transform var(--transition-normal);
      gap: var(--space-2);
      z-index: var(--z-fixed);
    }

    .nav-links.open {
      transform: translateX(0);
    }

    .nav-links a {
      padding: var(--space-4);
      font-size: var(--text-base);
      border-radius: var(--radius-lg);
      width: 100%;
      text-align: center;
    }

    .nav-indicator {
      display: none;
    }

    .btn-cta {
      margin-top: var(--space-4);
      padding: var(--space-4) var(--space-8) !important;
      font-size: var(--text-base) !important;
      width: 100%;
      text-align: center;
    }

    .mobile-menu-btn.open .hamburger:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }

    .mobile-menu-btn.open .hamburger:nth-child(2) {
      opacity: 0;
      transform: scaleX(0);
    }

    .mobile-menu-btn.open .hamburger:nth-child(3) {
      transform: rotate(-45deg) translate(5px, -5px);
    }

    .mobile-overlay {
      display: block;
    }

    .mobile-overlay.active {
      opacity: 1;
    }
  }
</style>