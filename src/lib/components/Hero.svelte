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
  <div class="container fade-in">
    <div class="hero-content">
      <div class="hero-text">
        <h1>Pondok Pesantren Kreatif <span>Al-Muhsinin</span></h1>
        <p class="subtitle">إِنَّ رَحْمَتَ ٱللَّهِ قَرِيبٌ مِّنَ ٱلْمُحْسِنِينَ
</p>
        <p class="subtitle">Sesungguhnya rahmat Allah amat dekat kepada orang-orang yang berbuat baik. *Surah Al-A'raf Ayat 56*
          </p>
        <p class="typing-text">Kegiatan: <span>{typedText}</span><span class="cursor">|</span></p>
        <div class="hero-buttons">
          <a href="#contact" class="btn">Daftar Sekarang</a>
          <a href="#activities" class="btn btn-outline">Lihat Kegiatan</a>
        </div>
      </div>
      <div class="hero-image">
        <img src="/abi.jpeg" alt="Pesantren Al-Muhsinin" />
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    padding-top: 120px;
    background: linear-gradient(135deg, #f5f7fa 0%, #e4f0f5 100%);
  }
  
  .hero-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 50px;
  }
  
  .hero-text {
    flex: 1;
  }
  
  .hero-image {
    flex: 1;
    text-align: center;
  }
  
  .hero-image img {
    max-width: 100%;
    border-radius: 10px;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  }
  
  h1 {
    font-size: 3rem;
    margin-bottom: 20px;
    color: var(--dark);
  }
  
  h1 span {
    color: var(--primary);
  }
  
  .subtitle {
    font-size: 1.2rem;
    color: var(--gray);
    margin-bottom: 30px;
  }
  
  .typing-text {
    font-size: 1.2rem;
    margin-bottom: 30px;
    min-height: 2rem;
  }
  
  .typing-text span:first-child {
    color: var(--primary);
    font-weight: 500;
  }
  
  .cursor {
    animation: blink 1s infinite;
  }

  /* Animasi Fade-In */
.fade-in {
  opacity: 0; /* Mulai dengan opacity 0 (tidak terlihat) */
  animation: fadeIn 1s ease-out forwards;
}

@keyframes fadeIn {
  0% {
    opacity: 0; /* Awal: opacity 0 */
  }
  100% {
    opacity: 1; /* Akhir: opacity 1 */
  }
}
  
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }
  
  .hero-buttons {
    display: flex;
    gap: 20px;
    margin-top: 40px;
  }
  
  @media (max-width: 992px) {
    h1 {
      font-size: 2.5rem;
    }
  }
  
  @media (max-width: 768px) {
    .hero-content {
      flex-direction: column;
    }
    
    .hero-text {
      order: 2;
      text-align: center;
    }
    
    .hero-image {
      order: 1;
    }
    
    .hero-buttons {
      justify-content: center;
    }
    
    h1 {
      font-size: 2rem;
    }
  }
  
  @media (max-width: 576px) {
    .hero-buttons {
      flex-direction: column;
      align-items: center;
    }
  }
</style>