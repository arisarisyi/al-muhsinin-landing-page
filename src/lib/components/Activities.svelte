<script lang="ts">
  import { activities } from '../data/activities';
</script>

<section id="activities" class="activities">
  <div class="container">
    <div class="section-title">
      <h2>Kegiatan Pesantren</h2>
      <p>Program unggulan yang membentuk karakter dan kompetensi santri</p>
    </div>

    <div class="activities-grid">
      {#each activities as activity, index}
        <div class="activity-card" style="animation-delay: {index * 0.1}s">
          <div class="activity-number">0{index + 1}</div>
          <div class="activity-icon">
            <i class={activity.icon}></i>
          </div>
          <h3>{activity.title}</h3>
          <p>{activity.description}</p>
          <div class="card-decoration"></div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .activities {
    background: linear-gradient(180deg, var(--white) 0%, var(--secondary) 100%);
    position: relative;
    overflow: hidden;
  }

  .activities::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--primary), transparent);
  }

  .activities-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: var(--space-8);
  }

  .activity-card {
    position: relative;
    background: var(--white);
    border-radius: var(--radius-2xl);
    padding: var(--space-8);
    text-align: center;
    box-shadow: var(--shadow-lg);
    transition: all var(--transition-normal);
    overflow: hidden;
    animation: fadeInUp 0.6s ease-out both;
  }

  .activity-card:hover {
    transform: translateY(-8px);
    box-shadow: var(--shadow-primary-lg);
  }

  .activity-number {
    position: absolute;
    top: var(--space-4);
    right: var(--space-4);
    font-size: var(--text-4xl);
    font-weight: 900;
    color: var(--gray-100);
    line-height: 1;
  }

  .activity-icon {
    position: relative;
    width: 90px;
    height: 90px;
    margin: 0 auto var(--space-6);
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    border-radius: var(--radius-2xl);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: var(--text-4xl);
    color: var(--white);
    box-shadow: var(--shadow-md);
    transition: all var(--transition-normal);
  }

  .activity-card:hover .activity-icon {
    transform: scale(1.1) rotate(5deg);
    box-shadow: var(--shadow-primary);
  }

  .activity-card h3 {
    font-size: var(--text-2xl);
    color: var(--gray-900);
    margin-bottom: var(--space-4);
    font-weight: 700;
  }

  .activity-card p {
    color: var(--gray-600);
    font-size: var(--text-base);
    line-height: 1.7;
    margin: 0;
  }

  .card-decoration {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary), var(--primary-light));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform var(--transition-normal);
  }

  .activity-card:hover .card-decoration {
    transform: scaleX(1);
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

  @media (max-width: 1024px) {
    .activities-grid {
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: var(--space-6);
    }
  }

  @media (max-width: 640px) {
    .activities-grid {
      grid-template-columns: 1fr;
    }

    .activity-card {
      padding: var(--space-6);
    }

    .activity-icon {
      width: 75px;
      height: 75px;
      font-size: var(--text-3xl);
    }
  }
</style>
