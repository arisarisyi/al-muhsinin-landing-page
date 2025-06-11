<script>
  import { activities } from '../data/activities';
</script>

<section id="activities" class="activities">
  <div class="container">
    <div class="section-title">
      <h2>Kegiatan Pesantren</h2>
    </div>
    
    <div class="activities-grid">
      {#each activities as activity}
        <div class="activity-card">
          <div class="activity-icon">
            <i class={activity.icon}></i>
          </div>
          <h3>{activity.title}</h3>
          <p>{activity.description}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .activities {
    background-color: var(--secondary);
  }
  
  .activities-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
  }
  
  .activity-card {
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    text-align: center;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .activity-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 15px 30px rgba(5, 163, 35, 0.1);
  }
  
  .activity-icon {
    width: 80px;
    height: 80px;
    margin: 0 auto 20px;
    background-color: rgba(5, 163, 35, 0.1);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    color: var(--primary);
  }
  
  .activity-card h3 {
    margin-bottom: 15px;
    font-size: 1.5rem;
  }
  
  @media (max-width: 768px) {
    .activities-grid {
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    }
  }
</style>