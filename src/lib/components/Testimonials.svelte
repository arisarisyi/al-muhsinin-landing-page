<script lang="ts">
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
  <div class="container">
    <div class="section-title">
      <h2>Apa Kata Alumni?</h2>
      <p>Pengalaman mereka selama berada di Pondok Pesantren Al-Muhsinin</p>
    </div>

    <div class="testimonials-wrapper">
      <button
        class="nav-arrow nav-prev"
        on:click={prevTestimonial}
        aria-label="Previous testimonial"
      >
        <i class="fas fa-chevron-left"></i>
      </button>

      <div class="testimonial-card">
        <div class="quote-bg">
          <i class="fas fa-quote-right"></i>
        </div>

        <div class="testimonial-content">
          <div class="testimonial-image">
            <img src={testimonials[activeTestimonial].image} alt={testimonials[activeTestimonial].name} />
            <div class="image-ring"></div>
          </div>

          <div class="testimonial-text">
            <p>{testimonials[activeTestimonial].quote}</p>

            <div class="testimonial-author">
              <h4>{testimonials[activeTestimonial].name}</h4>
              <span>{testimonials[activeTestimonial].role}</span>
            </div>
          </div>
        </div>
      </div>

      <button
        class="nav-arrow nav-next"
        on:click={nextTestimonial}
        aria-label="Next testimonial"
      >
        <i class="fas fa-chevron-right"></i>
      </button>
    </div>

    <div class="testimonial-dots">
      {#each testimonials as _, i}
        <button
          class="dot"
          class:active={i === activeTestimonial}
          on:click={() => activeTestimonial = i}
          aria-label="Go to testimonial {i + 1}"
        ></button>
      {/each}
    </div>
  </div>
</section>

<style>
  .testimonials {
    background: linear-gradient(180deg, var(--secondary) 0%, var(--white) 100%);
    position: relative;
    overflow: hidden;
  }

  .testimonials::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: radial-gradient(circle at 20% 80%, rgba(13, 148, 136, 0.05) 0%, transparent 50%),
                      radial-gradient(circle at 80% 20%, rgba(13, 148, 136, 0.05) 0%, transparent 50%);
    pointer-events: none;
  }

  .testimonials-wrapper {
    display: flex;
    align-items: center;
    gap: var(--space-6);
    position: relative;
  }

  .nav-arrow {
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
    box-shadow: var(--shadow-md);
    z-index: 2;
  }

  .nav-arrow:hover {
    background: var(--primary);
    border-color: var(--primary);
    color: var(--white);
    transform: scale(1.1);
    box-shadow: var(--shadow-primary);
  }

  .nav-arrow:active {
    transform: scale(1.05);
  }

  .testimonial-card {
    flex: 1;
    background: var(--white);
    border-radius: var(--radius-2xl);
    box-shadow: var(--shadow-xl);
    padding: var(--space-12);
    position: relative;
    overflow: hidden;
  }

  .quote-bg {
    position: absolute;
    top: var(--space-8);
    right: var(--space-8);
    font-size: 150px;
    color: var(--gray-100);
    line-height: 1;
    z-index: 0;
  }

  .testimonial-content {
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    gap: var(--space-10);
  }

  .testimonial-image {
    flex-shrink: 0;
    position: relative;
    width: 180px;
    height: 180px;
  }

  .testimonial-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: var(--radius-full);
    box-shadow: var(--shadow-lg);
    position: relative;
    z-index: 2;
  }

  .image-ring {
    position: absolute;
    inset: -8px;
    border: 3px solid var(--primary);
    border-radius: var(--radius-full);
    opacity: 0.2;
    z-index: 1;
  }

  .testimonial-text {
    flex: 1;
  }

  .testimonial-text p {
    font-size: var(--text-lg);
    color: var(--gray-600);
    line-height: 1.8;
    font-style: italic;
    margin-bottom: var(--space-6);
    position: relative;
  }

  .testimonial-text p::before {
    content: '"';
    font-size: var(--text-4xl);
    color: var(--primary);
    line-height: 0;
    vertical-align: -10px;
    margin-right: var(--space-2);
  }

  .testimonial-author h4 {
    font-size: var(--text-xl);
    color: var(--gray-900);
    margin-bottom: var(--space-1);
  }

  .testimonial-author span {
    display: inline-block;
    padding: var(--space-1) var(--space-3);
    background: linear-gradient(135deg, rgba(13, 148, 136, 0.1), rgba(13, 148, 136, 0.05));
    color: var(--primary);
    font-size: var(--text-sm);
    font-weight: 600;
    border-radius: var(--radius-full);
  }

  .testimonial-dots {
    display: flex;
    justify-content: center;
    gap: var(--space-3);
    margin-top: var(--space-10);
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
    .testimonial-content {
      flex-direction: column;
      text-align: center;
      gap: var(--space-8);
    }

    .testimonial-image {
      width: 150px;
      height: 150px;
    }

    .quote-bg {
      font-size: 100px;
    }
  }

  @media (max-width: 768px) {
    .testimonials-wrapper {
      flex-direction: column;
    }

    .nav-arrow {
      width: 48px;
      height: 48px;
    }

    .nav-prev {
      order: 2;
    }

    .nav-next {
      order: 3;
    }

    .testimonial-card {
      order: 1;
      width: 100%;
      padding: var(--space-8);
    }

    .testimonial-dots {
      order: 4;
      margin-top: var(--space-8);
    }
  }

  @media (max-width: 640px) {
    .testimonial-text p {
      font-size: var(--text-base);
    }

    .testimonial-image {
      width: 120px;
      height: 120px;
    }

    .testimonial-author h4 {
      font-size: var(--text-lg);
    }

    .quote-bg {
      font-size: 80px;
      top: var(--space-4);
      right: var(--space-4);
    }
  }
</style>
