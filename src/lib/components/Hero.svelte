<script lang="ts">
  import { onMount } from 'svelte';

  let typedText = '';
  const texts = ["Sholat Jamaah", "Pengajian Kitab Kuning", "1 Day 1 Juz", "Ilmu Hikmah", "Kewirausahaan"];
  let currentIndex = 0;
  let isDeleting = false;
  let typingSpeed = 100;

  onMount(() => {
    const type = () => {
      const currentText = texts[currentIndex];

      if (isDeleting) {
        typedText = currentText.substring(0, typedText.length - 1);
        typingSpeed = 50;
      } else {
        typedText = currentText.substring(0, typedText.length + 1);
        typingSpeed = 100;
      }

      if (!isDeleting && typedText === currentText) {
        typingSpeed = 1500;
        isDeleting = true;
      } else if (isDeleting && typedText === '') {
        isDeleting = false;
        currentIndex = (currentIndex + 1) % texts.length;
        typingSpeed = 500;
      }

      setTimeout(type, typingSpeed);
    };

    setTimeout(type, 1000);
  });
</script>

<section id="home" class="hero">
  <div class="hero-bg">
    <div class="hero-gradient"></div>
    <div class="hero-pattern"></div>
  </div>

  <div class="container">
    <div class="hero-content">
      <div class="hero-text">
        <div class="hero-badge">
          <i class="fas fa-star"></i>
          <span>Pesantren Modern untuk Mahasiswa</span>
        </div>

        <h1 class="hero-title">
          Pondok Pesantren Kreatif
          <span class="highlight">Al-Muhsinin</span>
        </h1>

        <div class="hero-verse">
          <p class="arabic">إِنَّ رَحْمَتَ ٱللَّهِ قَرِيبٌ مِّنَ ٱلْمُحْسِنِينَ</p>
          <p class="translation">"Sesungguhnya rahmat Allah amat dekat kepada orang-orang yang berbuat baik."</p>
          <p class="source">(QS. Al-A'raf: 56)</p>
        </div>

        <div class="typing-section">
          <span class="typing-label">Kegiatan Unggulan:</span>
          <span class="typing-text">{typedText}</span>
          <span class="cursor">|</span>
        </div>

        <div class="hero-buttons">
          <a href="#contact" class="btn btn-primary btn-lg">
            <span>Daftar Sekarang</span>
            <i class="fas fa-arrow-right"></i>
          </a>
          <a href="#activities" class="btn btn-outline btn-lg">
            <span>Lihat Kegiatan</span>
          </a>
        </div>

        <div class="hero-stats">
          <div class="stat-item">
            <div class="stat-number">2014</div>
            <div class="stat-label">Tahun Berdiri</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">100+</div>
            <div class="stat-label">Santri Aktif</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">5+</div>
            <div class="stat-label">Program Unggulan</div>
          </div>
        </div>
      </div>

      <div class="hero-image">
        <div class="image-wrapper">
          <img src="/abi.jpeg" alt="Pondok Pesantren Al-Muhsinin" />
        </div>
      </div>
    </div>
  </div>

  <div class="hero-scroll">
    <div class="scroll-indicator">
      <span>Scroll Down</span>
      <i class="fas fa-chevron-down"></i>
    </div>
  </div>
</section>

<style>
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding-top: var(--space-24);
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    z-index: 0;
  }

  .hero-gradient {
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--secondary) 0%, var(--gray-50) 100%);
  }

  .hero-pattern {
    position: absolute;
    inset: 0;
    opacity: 0.03;
    background-image:
      radial-gradient(circle at 25% 25%, var(--primary) 2%, transparent 2%),
      radial-gradient(circle at 75% 75%, var(--primary) 2%, transparent 2%);
    background-size: 40px 40px;
  }

  .hero-content {
    position: relative;
    z-index: 1;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--space-16);
    align-items: center;
  }

  .hero-text {
    animation: fadeInUp 0.8s ease-out;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: var(--space-2);
    padding: var(--space-2) var(--space-4);
    background: linear-gradient(135deg, rgba(13, 148, 136, 0.1), rgba(13, 148, 136, 0.05));
    border: 1px solid rgba(13, 148, 136, 0.2);
    border-radius: var(--radius-full);
    color: var(--primary);
    font-size: var(--text-sm);
    font-weight: 600;
    margin-bottom: var(--space-6);
  }

  .hero-badge i {
    color: var(--accent);
  }

  .hero-title {
    font-size: var(--text-6xl);
    font-weight: 900;
    line-height: 1.1;
    margin-bottom: var(--space-8);
    color: var(--gray-900);
  }

  .hero-title .highlight {
    display: block;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-verse {
    padding: var(--space-6);
    background: var(--white);
    border-radius: var(--radius-xl);
    box-shadow: var(--shadow-lg);
    border-left: 4px solid var(--primary);
    margin-bottom: var(--space-8);
  }

  .hero-verse .arabic {
    font-family: 'Traditional Arabic', 'Scheherazade', serif;
    font-size: var(--text-2xl);
    color: var(--primary);
    text-align: right;
    direction: rtl;
    margin-bottom: var(--space-3);
    line-height: 1.8;
  }

  .hero-verse .translation {
    font-size: var(--text-base);
    color: var(--gray-700);
    font-style: italic;
    margin-bottom: var(--space-2);
  }

  .hero-verse .source {
    font-size: var(--text-sm);
    color: var(--gray-500);
    font-weight: 600;
  }

  .typing-section {
    display: flex;
    align-items: center;
    gap: var(--space-2);
    margin-bottom: var(--space-8);
    flex-wrap: wrap;
  }

  .typing-label {
    font-size: var(--text-lg);
    font-weight: 600;
    color: var(--gray-700);
  }

  .typing-text {
    font-size: var(--text-xl);
    font-weight: 700;
    color: var(--primary);
  }

  .cursor {
    font-size: var(--text-xl);
    font-weight: 700;
    color: var(--primary);
    animation: blink 1s infinite;
  }

  .hero-buttons {
    display: flex;
    gap: var(--space-4);
    margin-bottom: var(--space-12);
  }

  .hero-buttons .btn i {
    font-size: var(--text-sm);
  }

  .hero-stats {
    display: flex;
    align-items: center;
    gap: var(--space-6);
    padding: var(--space-8);
    background: var(--white);
    border-radius: var(--radius-2xl);
    box-shadow: var(--shadow-lg);
  }

  .stat-item {
    text-align: center;
    flex: 1;
  }

  .stat-number {
    font-size: var(--text-3xl);
    font-weight: 800;
    color: var(--primary);
    margin-bottom: var(--space-1);
  }

  .stat-label {
    font-size: var(--text-sm);
    color: var(--gray-600);
    font-weight: 500;
  }

  .stat-divider {
    width: 1px;
    height: 40px;
    background: var(--gray-200);
  }

  .hero-image {
    animation: fadeInUp 0.8s ease-out 0.2s both;
  }

  .image-wrapper {
    position: relative;
    display: inline-block;
    width: 100%;
  }

  .image-border {
    position: absolute;
    inset: -20px;
    border: 3px solid var(--primary);
    border-radius: var(--radius-2xl);
    opacity: 0.2;
    z-index: 0;
  }

  .image-wrapper img {
    position: relative;
    width: 100%;
    height: auto;
    border-radius: var(--radius-2xl);
    box-shadow: var(--shadow-2xl);
    z-index: 1;
    transition: transform var(--transition-normal);
  }

  .image-wrapper:hover img {
    transform: scale(1.02);
  }

  .image-badge {
    position: absolute;
    bottom: var(--space-6);
    right: var(--space-6);
    display: flex;
    align-items: center;
    gap: var(--space-2);
    padding: var(--space-3) var(--space-6);
    background: linear-gradient(135deg, var(--accent), var(--accent-dark));
    color: var(--white);
    border-radius: var(--radius-full);
    font-weight: 600;
    box-shadow: var(--shadow-lg);
    z-index: 2;
  }

  .hero-scroll {
    position: absolute;
    bottom: var(--space-8);
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
  }

  .scroll-indicator {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-2);
    color: var(--gray-500);
    font-size: var(--text-xs);
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    animation: bounce 2s infinite;
  }

  .scroll-indicator i {
    font-size: var(--text-sm);
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  @keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
      transform: translateX(-50%) translateY(0);
    }
    40% {
      transform: translateX(-50%) translateY(-10px);
    }
    60% {
      transform: translateX(-50%) translateY(-5px);
    }
  }

  @media (max-width: 1024px) {
    .hero-title {
      font-size: var(--text-5xl);
    }

    .hero-content {
      gap: var(--space-12);
    }
  }

  @media (max-width: 768px) {
    .hero {
      padding-top: var(--space-20);
      min-height: auto;
    }

    .hero-content {
      grid-template-columns: 1fr;
      gap: var(--space-12);
    }

    .hero-text {
      order: 2;
    }

    .hero-image {
      order: 1;
    }

    .hero-title {
      font-size: var(--text-4xl);
    }

    .hero-verse {
      padding: var(--space-4);
    }

    .hero-verse .arabic {
      font-size: var(--text-xl);
    }

    .hero-buttons {
      flex-direction: column;
    }

    .hero-stats {
      flex-direction: column;
      gap: var(--space-4);
    }

    .stat-divider {
      width: 40px;
      height: 1px;
    }

    .image-border {
      display: none;
    }
  }

  @media (max-width: 640px) {
    .hero-title {
      font-size: var(--text-3xl);
    }

    .hero-verse .translation {
      font-size: var(--text-sm);
    }

    .typing-section {
      flex-direction: column;
      align-items: flex-start;
      gap: var(--space-1);
    }

    .hero-scroll {
      display: none;
    }
  }
</style>
