<script lang="ts">
	interface Props {
		id?: string;
}

	let { id }: Props = $props();
</script>

<section id={id ?? 'about'} class="about">
  <div class="container">
    <div class="section-title">
      <h2>Tentang Kami</h2>
      <p>Mengenal lebih dekat Pondok Pesantren Kreatif Al-Muhsinin</p>
    </div>

    <div class="about-content">
      <div class="about-image">
        <div class="image-wrapper">
          <img src="/gus-sholah.jpg" alt="KH. Sholahuddin Wahid" />
          <div class="image-caption">
            <div class="caption-icon">
              <i class="fas fa-quote-left"></i>
            </div>
            <p>Peresmian oleh KH. Sholahuddin Wahid</p>
          </div>
        </div>
      </div>

     <div class="about-text">
  <div class="about-intro">
    <h3>Pesantren Kreatif untuk Mahasiswa</h3>
    <p>
      Pondok Pesantren Kreatif Al-Muhsinin adalah pesantren untuk mahasiswa putra dan putri
      yang berlokasi di Cukir, Kecamatan Diwek, Kabupaten Jombang.
    </p>
  </div>

     <div class="timeline">
    <div class="timeline-item">
      <div class="timeline-icon">
        <i class="fas fa-calendar-alt"></i>
      </div>
      <div class="timeline-content">
        <h4>Tahun 2014</h4>
        <p>
          Pondok Pesantren Kreatif Al-Muhsinin didirikan pada tahun 2014 sebagai tempat bernaung
          bagi para mahasiswa yang telah lulus dari Pondok Pesantren Tebuireng, Jombang.
        </p>
      </div>
    </div>

   <div class="timeline-item">
      <div class="timeline-icon">
        <i class="fas fa-users"></i>
      </div>
      <div class="timeline-content">
        <h4>Mandat dan Restu Ulama</h4>
        <p>
          Pendirian pesantren ini merupakan hasil dari masukan dan dorongan para guru
          KH. Agus Maulana, di antaranya KH. Ishaq Latief dari Tebuireng dan
          Habib Abu Bakar bin Abbas (Mbah Wo) dari Banyuwangi.
        </p>
      </div>
    </div>

             <div class="timeline-item">
      <div class="timeline-icon">
        <i class="fas fa-certificate"></i>
      </div>
         <div class="timeline-content">
        <h4>Peresmian</h4>
        <p>
          Pondok ini diresmikan oleh Pengasuh Pondok Pesantren Tebuireng saat itu,
          KH. Sholahuddin Wahid — putra dari KH. Abdul Wahid Hasyim dan adik dari Gus Dur.
          Peresmian tersebut disertai doa dan restu dari para masyayikh Tebuireng serta
          para guru spiritual KH. Agus Maulana.
        </p>
      </div>
          </div>
        </div>

        <div class="vision-mission">
          <div class="vm-card">
            <div class="vm-icon">
              <i class="fas fa-eye"></i>
            </div>
            <h4>Visi</h4>
            <p>Menjadi pusat pendidikan Islam yang kreatif dan inovatif untuk mencetak generasi muslim yang berkualitas.</p>
          </div>

          <div class="vm-card">
            <div class="vm-icon">
              <i class="fas fa-bullseye"></i>
            </div>
            <h4>Misi</h4>
            <p>Menyelenggarakan pendidikan yang memadukan ilmu agama dan ilmu umum serta mengembangkan kreativitas santri.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .about {
    background: linear-gradient(180deg, var(--gray-50) 0%, var(--white) 100%);
    position: relative;
    overflow: hidden;
  }

  .about::before {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 40%;
    height: 100%;
    background: linear-gradient(135deg, var(--secondary) 0%, transparent 100%);
    opacity: 0.3;
  }

  .about-content {
    position: relative;
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: var(--space-16);
    align-items: start;
  }

  .about-image {
    position: relative;
  }

  .image-wrapper {
    position: relative;
    border-radius: var(--radius-2xl);
    overflow: hidden;
    box-shadow: var(--shadow-2xl);
  }

  .image-wrapper img {
    width: 100%;
    height: auto;
    display: block;
    transition: transform var(--transition-slow);
  }

  .image-wrapper:hover img {
    transform: scale(1.05);
  }

  .image-caption {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: var(--space-6);
    background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
    color: var(--white);
  }

  .caption-icon {
    font-size: var(--text-2xl);
    margin-bottom: var(--space-2);
    opacity: 0.8;
  }

  .image-caption p {
    margin: 0;
    font-size: var(--text-sm);
    font-weight: 500;
  }

  .about-text {
    display: flex;
    flex-direction: column;
    gap: var(--space-8);
  }

  .about-intro h3 {
    font-size: var(--text-3xl);
    color: var(--gray-900);
    margin-bottom: var(--space-4);
  }

  .about-intro p {
    font-size: var(--text-lg);
    color: var(--gray-600);
    line-height: 1.8;
  }

  .timeline {
    display: flex;
    flex-direction: column;
    gap: var(--space-6);
  }

  .timeline-item {
    display: flex;
    gap: var(--space-4);
    align-items: start;
  }

  .timeline-icon {
    flex-shrink: 0;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: var(--white);
    border-radius: var(--radius-xl);
    font-size: var(--text-lg);
    box-shadow: var(--shadow-md);
  }

  .timeline-content {
    flex: 1;
    padding: var(--space-5);
    background: var(--white);
    border-radius: var(--radius-xl);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-normal);
  }

  .timeline-content:hover {
    box-shadow: var(--shadow-md);
    transform: translateY(-2px);
  }

  .timeline-content h4 {
    font-size: var(--text-lg);
    color: var(--primary);
    margin-bottom: var(--space-2);
  }

  .timeline-content p {
    color: var(--gray-600);
    font-size: var(--text-base);
    margin: 0;
  }

  .vision-mission {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--space-6);
  }

  .vm-card {
    padding: var(--space-6);
    background: var(--white);
    border-radius: var(--radius-xl);
    box-shadow: var(--shadow-md);
    text-align: center;
    transition: all var(--transition-normal);
    border: 2px solid transparent;
  }

  .vm-card:hover {
    border-color: var(--primary);
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
  }

  .vm-icon {
    width: 60px;
    height: 60px;
    margin: 0 auto var(--space-4);
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(13, 148, 136, 0.1), rgba(13, 148, 136, 0.05));
    color: var(--primary);
    border-radius: var(--radius-full);
    font-size: var(--text-2xl);
  }

  .vm-card h4 {
    font-size: var(--text-xl);
    color: var(--gray-900);
    margin-bottom: var(--space-3);
  }

  .vm-card p {
    color: var(--gray-600);
    font-size: var(--text-sm);
    margin: 0;
  }

  @media (max-width: 1024px) {
    .about-content {
      grid-template-columns: 1fr;
      gap: var(--space-12);
    }

    .about-image {
      order: -1;
    }
  }

  @media (max-width: 768px) {
    .vision-mission {
      grid-template-columns: 1fr;
    }

    .timeline-item {
      flex-direction: column;
      gap: var(--space-3);
    }

    .timeline-icon {
      width: 45px;
      height: 45px;
    }
  }

  @media (max-width: 640px) {
    .about-intro h3 {
      font-size: var(--text-2xl);
    }

    .about-intro p {
      font-size: var(--text-base);
    }
  }
</style>
