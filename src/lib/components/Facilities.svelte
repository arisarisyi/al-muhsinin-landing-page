<script>
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
      <h2>Dokumentasi Kegiatan Pesantren</h2>
    </div>
    
    <div class="facilities-slider">
      <div class="slider-controls">
        <button aria-label="left" on:click={prevFacility} class="slider-arrow">
          <i class="fas fa-chevron-left"></i>
        </button>
      </div>
      
      <div class="slider-content">
        <div class="facility-info">
          <h3>{documentation[activeFacility].title}</h3>
          <p>{documentation[activeFacility].description}</p>
          <div class="facility-dots">
            {#each documentation as _, i}
              <span class:active={i === activeFacility} on:click={() => activeFacility = i}></span>
            {/each}
          </div>
        </div>
        
        <div class="facility-image">
          <img src={documentation[activeFacility].image} alt={documentation[activeFacility].title} />
        </div>
      </div>
      
      <div class="slider-controls">
        <button aria-label="next" on:click={nextFacility} class="slider-arrow">
          <i class="fas fa-chevron-right"></i>
        </button>
      </div>
    </div>
  </div>
</section>

<style>
  .facilities {
    background-color: var(--light);
  }
  
  .facilities-slider {
    display: flex;
    align-items: center;
    gap: 30px;
  }
  
  .slider-content {
    flex: 1;
    display: flex;
    align-items: center;
    gap: 50px;
  }
  
  .facility-info {
    flex: 1;
  }
  
  .facility-info h3 {
    font-size: 2rem;
    margin-bottom: 20px;
    color: var(--primary);
  }
  
  .facility-info p {
    font-size: 1.1rem;
    margin-bottom: 30px;
    color: var(--gray);
  }
  
  .facility-image {
    flex: 1;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  }
  
  .facility-image img {
    width: 100%;
    height: auto;
    display: block;
    transition: transform 0.5s ease;
  }
  
  .slider-arrow {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: white;
    border: none;
    color: var(--primary);
    font-size: 1.2rem;
    cursor: pointer;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }
  
  .slider-arrow:hover {
    background-color: var(--primary);
    color: white;
  }
  
  .facility-dots {
    display: flex;
    gap: 10px;
  }
  
  .facility-dots span {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: #ddd;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .facility-dots span.active {
    background-color: var(--primary);
    transform: scale(1.2);
  }
  
  @media (max-width: 992px) {
    .slider-content {
      flex-direction: column;
    }
    
    .facility-info {
      order: 2;
      text-align: center;
    }
    
    .facility-image {
      order: 1;
    }
    
    .facility-dots {
      justify-content: center;
    }
  }

  @media (max-width: 768px) {
  .facilities-slider {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .slider-content {
    flex-direction: column;
    align-items: center;
  }

  .facility-info,
  .facility-image {
    width: 100%;
  }

  .facility-dots {
    margin-top: 20px;
    justify-content: center;
  }

  .slider-controls {
    margin: 10px 0;
    display: flex;
    justify-content: center;
  }
}
  
  @media (max-width: 576px) {
    .facility-info h3 {
      font-size: 1.5rem;
    }
  }
</style>