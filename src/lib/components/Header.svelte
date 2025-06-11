<script lang="ts">
  export let scrollTo: (id: string) => void;
  export let activeSection: string;
  
  let mobileMenuOpen = false;
  
  const toggleMenu = () => {
    mobileMenuOpen = !mobileMenuOpen;
  };
</script>

<header>
  <div class="container">
    <div class="header-inner">
      <div class="logo">
        <img src='./static/images/al-muhsinin.png' alt="Logo Al-Muhsinin" />
        <span>Al-Muhsinin</span>
      </div>
      
      <nav class={`nav-links ${mobileMenuOpen ? 'open' : ''}`}>
        <a href="#home" class:active={activeSection === 'home'} on:click|preventDefault={() => scrollTo('home')}>Beranda</a>
        <a href="#about" class:active={activeSection === 'about'} on:click|preventDefault={() => scrollTo('about')}>Tentang</a>
        <a href="#activities" class:active={activeSection === 'activities'} on:click|preventDefault={() => scrollTo('activities')}>Kegiatan</a>
        <a href="#facilities" class:active={activeSection === 'facilities'} on:click|preventDefault={() => scrollTo('facilities')}>Dokumen Kegiatan</a>
        <a href="#testimonials" class:active={activeSection === 'testimonials'} on:click|preventDefault={() => scrollTo('testimonials')}>Testimoni</a>
        <a href="#contact" class:active={activeSection === 'contact'} on:click|preventDefault={() => scrollTo('contact')}>Kontak</a>
      </nav>

      <div
        class="mobile-menu-btn"
        on:click={toggleMenu}
        on:keydown={(e) => e.key === 'Enter' && toggleMenu()}
        role="button"
        tabindex="0"
        aria-label="Toggle mobile menu"
      >
        <i class={`fas ${mobileMenuOpen ? 'fa-times' : 'fa-bars'}`}></i>
      </div>
    </div>
  </div>
</header>

<style>
  header {
    background-color: white;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    position: fixed;
    width: 100%;
    top: 0;
    left: 0;
    z-index: 1000;
    transition: all 0.3s ease;
  }
  
  .header-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 20px;
  }
  
  .logo {
    display: flex;
    align-items: center;
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--primary);
    text-decoration: none;
  }
  
  .logo img {
    height: 40px;
    margin-right: 10px;
  }
  
  .nav-links {
    display: flex;
    align-items: center;
  }
  
  .nav-links a {
    margin-left: 30px;
    color: var(--dark);
    text-decoration: none;
    font-weight: 500;
    transition: color 0.3s ease;
    position: relative;
  }
  
  .nav-links a:hover, .nav-links a.active {
    color: var(--primary);
  }
  
  .nav-links a.active::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: var(--primary);
  }
  
  .mobile-menu-btn {
    display: none;
    font-size: 1.5rem;
    color: var(--dark);
    cursor: pointer;
  }
  
  @media (max-width: 768px) {
    .mobile-menu-btn {
      display: block;
    }
    
    .nav-links {
      position: fixed;
      top: 80px;
      left: 0;
      width: 100%;
      background-color: white;
      flex-direction: column;
      align-items: center;
      padding: 20px 0;
      box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
      transform: translateY(-150%);
      transition: transform 0.3s ease;
    }
    
    .nav-links.open {
      transform: translateY(0);
    }
    
    .nav-links a {
      margin: 15px 0;
    }
  }
</style>