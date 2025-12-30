<script lang="ts">
 import { documentation } from '../data/documentation';

  let activeFacility = 0;

  const nextFacility = () => {
    activeFacility = (activeFacility + 1) % documentation.length;
  };

  const prevFacility = () => {
    activeFacility = (activeFacility - 1 + documentation.length) % documentation.length;
  };
</script>

<section id="facilities" class="facilities">
  <div class="container">
    <div class="section-title">
      <h2>Dokumentasi Kegiatan</h2>
      <p>Momen-momen berharga dalam perjalanan Pondok Pesantren Al-Muhsinin</p>
    </div>

    <div class="facilities-wrapper">
      <button
        class="slider-nav nav-prev"
        on:click={prevFacility}
        aria-label="Previous documentation"
      >
        <i class="fas fa-chevron-left"></i>
      </button>

      <div class="slider-container">
        {#each documentation as doc, index}
          <div class="slide" class:active={index === activeFacility}>
            <div class="slide-content">
              <div class="slide-image">
                <div class="image-wrapper">
                  <img src={doc.image} alt={doc.title} />
                  <div class="image-overlay"></div>
                </div>
              </div>

              <div class="slide-info">
                <div class="info-badge">
                  <i class="fas fa-camera"></i>
                  <span>Dokumentasi</span>
                </div>
                <h3>{doc.title}</h3>
                <p>{doc.description}</p>
              </div>
            </div>
          </div>
        {/each}
      </div>

      <button
        class="slider-nav nav-next"
        on:click={nextFacility}
        aria-label="Next documentation"
      >
        <i class="fas fa-chevron-right"></i>
      </button>
    </div>

    <div class="slider-dots">
      {#each documentation as _, i}
        <button
          class="dot"
          class:active={i === activeFacility}
          on:click={() => activeFacility = i}
          aria-label="Go to slide {i + 1}"
        ></button>
      {/each}
    </div>
  </div>
</section>

<style>
  .facilities {
    background: var(--gray-50);
    position: relative;
    overflow: hidden;
  }

  .facilities-wrapper {
    display: flex;
    align-items: center;
    gap: var(--space-6);
    position: relative;
  }

  .slider-nav {
    flex-shrink: 0;
    width: 56px;
    height: 56px;
    border-radius: var(--radius-full);
    background: var(--white);
    border: 2px solid var(--gray-200);
    color: var(--gray-700);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all var(--transition-normal);
    z-index: 2;
  }

  .slider-nav:hover {
    background: var(--primary);
    border-color: var(--primary);
    color: var(--white);
    transform: scale(1.1);
    box-shadow: var(--shadow-primary);
  }

  .slider-nav:active {
    transform: scale(1.05);
  }

  .slider-container {
    flex: 1;
    position: relative;
    overflow: hidden;
    border-radius: var(--radius-2xl);
    height: 400px;
  }

  .slide {
    position: absolute;
    inset: 0;
    opacity: 0;
    transform: translateX(100%);
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    pointer-events: none;
    height: 100%;
  }

  .slide.active {
    opacity: 1;
    transform: translateX(0);
    pointer-events: auto;
  }

  .slide-content {
    display: grid;
    grid-template-columns: 1.2fr 0.8fr;
    gap: 0;
    background: var(--white);
    border-radius: var(--radius-2xl);
    overflow: hidden;
    box-shadow: var(--shadow-xl);
    height: 100%;
  }

  .slide-image {
    position: relative;
    overflow: hidden;
  }

  .image-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
  }

  .image-wrapper img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform var(--transition-slow);
  }

  .slide.active .image-wrapper img {
    transform: scale(1.05);
  }

  .image-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to right, transparent 50%, rgba(0, 0, 0, 0.1));
  }

  .slide-info {
    padding: var(--space-10);
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .info-badge {
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
    width: fit-content;
    margin-bottom: var(--space-6);
  }

  .slide-info h3 {
    font-size: var(--text-3xl);
    color: var(--gray-900);
    margin-bottom: var(--space-4);
    line-height: 1.3;
  }

  .slide-info p {
    font-size: var(--text-lg);
    color: var(--gray-600);
    line-height: 1.7;
  }

  .slider-dots {
    display: flex;
    justify-content: center;
    gap: var(--space-3);
    margin-top: var(--space-8);
  }

  .dot {
    width: 12px;
    height: 12px;
    border-radius: var(--radius-full);
    background: var(--gray-300);
    border: none;
    cursor: pointer;
    transition: all var(--transition-normal);
  }

  .dot:hover {
    background: var(--primary);
    transform: scale(1.2);
  }

  .dot.active {
    background: var(--primary);
    width: 32px;
    border-radius: var(--radius-full);
  }

  @media (max-width: 1024px) {
    .slider-container {
      height: 500px;
    }

    .slide-content {
      grid-template-columns: 1fr;
      grid-template-rows: 300px auto;
    }

    .image-overlay {
      background: linear-gradient(to bottom, transparent 50%, rgba(0, 0, 0, 0.1));
    }

    .slide-info {
      padding: var(--space-8);
    }
  }

  @media (max-width: 768px) {
    .facilities-wrapper {
      flex-direction: column;
    }

    .slider-nav {
      width: 48px;
      height: 48px;
    }

    .nav-prev {
      order: 2;
    }

    .nav-next {
      order: 3;
    }

    .slider-container {
      order: 1;
      width: 100%;
      height: auto;
      min-height: 480px;
    }

    .slide-content {
      grid-template-rows: 300px auto;
    }

    .slide-info {
      padding: var(--space-6);
    }

    .slide-info h3 {
      font-size: var(--text-2xl);
    }

    .slide-info p {
      font-size: var(--text-base);
    }

    .slider-dots {
      order: 4;
      margin-top: var(--space-6);
    }
  }

  @media (max-width: 640px) {
    .slider-container {
      min-height: 450px;
    }

    .slide-content {
      grid-template-rows: 260px auto;
    }

    .slide-info {
      padding: var(--space-5);
    }

    .slide-info h3 {
      font-size: var(--text-xl);
      margin-bottom: var(--space-3);
    }

    .slide-info p {
      font-size: var(--text-sm);
      line-height: 1.6;
    }

    .info-badge {
      margin-bottom: var(--space-4);
      font-size: var(--text-xs);
    }

    .slider-dots {
      margin-top: var(--space-5);
    }

    .dot {
      width: 10px;
      height: 10px;
    }

    .dot.active {
      width: 28px;
    }
  }
</style>
