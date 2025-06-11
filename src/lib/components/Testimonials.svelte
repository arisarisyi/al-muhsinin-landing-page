<script>
import {testimonials} from '../data/testimonials.js';
  
  let activeTestimonial = 0;
  
  const nextTestimonial = () => {
    activeTestimonial = (activeTestimonial + 1) % testimonials.length;
  };
  
  const prevTestimonial = () => {
    activeTestimonial = (activeTestimonial - 1 + testimonials.length) % testimonials.length;
  };
</script>

<section id="testimonials" class="testimonials">
  <div class="container fade-in">
    <div class="section-title">
      <h2>Apa Kata Alumni?</h2>
    </div>
    
    <div class="testimonial-slider">
      <button aria-label="prev" on:click={prevTestimonial} class="slider-arrow">
        <i class="fas fa-chevron-left"></i>
      </button>
      
      <div class="testimonial-content">
        <div class="testimonial-image">
          <img src={testimonials[activeTestimonial].image} alt={testimonials[activeTestimonial].name} />
        </div>
        
        <div class="testimonial-text">
          <div class="quote-icon">
            <i class="fas fa-quote-left"></i>
          </div>
          <p>{testimonials[activeTestimonial].quote}</p>
          <div class="testimonial-author">
            <h4>{testimonials[activeTestimonial].name}</h4>
            <span>{testimonials[activeTestimonial].role}</span>
          </div>
        </div>
      </div>
      
      <button aria-label="right" on:click={nextTestimonial} class="slider-arrow">
        <i class="fas fa-chevron-right"></i>
      </button>
    </div>
    
    <div class="testimonial-dots">
      {#each testimonials as _, i}
        <span class:active={i === activeTestimonial} on:click={() => activeTestimonial = i}></span>
      {/each}
    </div>
  </div>
</section>

<style>
  .testimonials {
    background-color: var(--secondary);
  }
  
  .testimonial-slider {
    display: flex;
    align-items: center;
    gap: 30px;
  }
  
  .testimonial-content {
    flex: 1;
    display: flex;
    align-items: center;
    gap: 50px;
    padding: 30px;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  }
  
  .testimonial-image {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    overflow: hidden;
    border: 5px solid var(--primary);
  }
  
  .testimonial-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .testimonial-text {
    flex: 1;
    position: relative;
  }
  
  .quote-icon {
    position: absolute;
    top: -20px;
    left: -30px;
    font-size: 4rem;
    color: rgba(5, 163, 35, 0.1);
    z-index: 0;
  }
  
  .testimonial-text p {
    font-size: 1.1rem;
    font-style: italic;
    color: var(--gray);
    margin-bottom: 20px;
    position: relative;
    z-index: 1;
  }
  
  .testimonial-author h4 {
    font-size: 1.3rem;
    color: var(--primary);
    margin-bottom: 5px;
  }
  
  .testimonial-author span {
    color: var(--gray);
    font-size: 0.9rem;
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
  
  .testimonial-dots {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 30px;
  }
  
  .testimonial-dots span {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: #ddd;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .testimonial-dots span.active {
    background-color: var(--primary);
    transform: scale(1.2);
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
  
  @media (max-width: 992px) {
    .testimonial-content {
      flex-direction: column;
      text-align: center;
    }
    
    .quote-icon {
      left: 50%;
      transform: translateX(-50%);
      top: -10px;
    }
  }
  
  @media (max-width: 576px) {
    .testimonial-image {
      width: 150px;
      height: 150px;
    }
  }
</style>