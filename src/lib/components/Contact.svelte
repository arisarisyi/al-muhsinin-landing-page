<script lang="ts">
</script>

<section id="contact" class="contact">
  <div class="container">
    <div class="section-title">
      <h2>Hubungi Kami</h2>
      <p>Informasi pendaftaran dan lokasi Pondok Pesantren Al-Muhsinin</p>
    </div>

    <div class="contact-content">
      <div class="contact-info">
        <div class="info-header">
          <h3>Informasi Kontak</h3>
          <p>Hubungi kami untuk informasi lebih lanjut</p>
        </div>

        <div class="info-cards">
          <div class="info-card">
            <div class="card-icon">
              <i class="fas fa-map-marker-alt"></i>
            </div>
            <div class="card-content">
              <h4>Alamat</h4>
              <p>Dsn.Cukir Gang III 02/02 Cukir Diwek Kab. Jombang</p>
            </div>
          </div>

          <div class="info-card">
            <div class="card-icon">
              <i class="fas fa-phone-alt"></i>
            </div>
            <div class="card-content">
              <h4>Telepon / WhatsApp</h4>
              <p>+62 8123 4439 793</p>
            </div>
          </div>

          <a
            href="https://api.whatsapp.com/send/?phone=6281234439793&text&type=phone_number&app_absent=0"
            target="_blank"
            rel="noopener noreferrer"
            class="cta-button"
          >
            <i class="fab fa-whatsapp"></i>
            <span>Chat via WhatsApp</span>
          </a>
        </div>
      </div>

      <div class="contact-brosur">
        <div class="brosur-header">
          <h3>Brosur Pendaftaran</h3>
          <p>Download brosur untuk informasi lengkap</p>
        </div>

        <a href="./brosur.jpeg" target="_blank" rel="noopener noreferrer" class="brosur-card">
          <div class="brosur-preview">
            <img src="./brosur.jpeg" alt="Brosur Pendaftaran" />
            <div class="brosur-overlay">
              <i class="fas fa-download"></i>
              <span>Klik untuk memperbesar</span>
            </div>
          </div>
          <div class="brosur-action">
            <i class="fas fa-file-pdf"></i>
            <span>Lihat Brosur Lengkap</span>
          </div>
        </a>
      </div>
    </div>

    <div class="map-section">
      <div class="map-container">
        <iframe
          title="Pondok Pesantren Al-Muhsinin Location"
          width="100%"
          height="400"
          style="border:0;"
          loading="lazy"
          allowfullscreen
          referrerpolicy="no-referrer-when-downgrade"
          src="https://www.google.com/maps?q=-7.616136550143975,112.2371978698461&z=15&output=embed">
        </iframe>
      </div>
    </div>
  </div>
</section>

<style>
  .contact {
    background: linear-gradient(180deg, var(--white) 0%, var(--gray-50) 100%);
    position: relative;
  }

  .contact-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--space-12);
    margin-bottom: var(--space-12);
  }

  .info-header {
    margin-bottom: var(--space-8);
  }

  .info-header h3 {
    font-size: var(--text-3xl);
    color: var(--gray-900);
    margin-bottom: var(--space-2);
  }

  .info-header p {
    color: var(--gray-600);
    font-size: var(--text-lg);
    margin: 0;
  }

  .info-cards {
    display: flex;
    flex-direction: column;
    gap: var(--space-6);
  }

  .info-card {
    display: flex;
    gap: var(--space-4);
    padding: var(--space-6);
    background: var(--white);
    border-radius: var(--radius-xl);
    box-shadow: var(--shadow-md);
    transition: all var(--transition-normal);
  }

  .info-card:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg);
  }

  .card-icon {
    flex-shrink: 0;
    width: 56px;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: var(--white);
    border-radius: var(--radius-xl);
    font-size: var(--text-xl);
  }

  .card-content h4 {
    font-size: var(--text-lg);
    color: var(--gray-900);
    margin-bottom: var(--space-2);
  }

  .card-content p {
    color: var(--gray-600);
    margin: 0;
  }

  .cta-button {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: var(--space-3);
    padding: var(--space-5);
    background: linear-gradient(135deg, #25D366, #128C7E);
    color: var(--white);
    border-radius: var(--radius-xl);
    text-decoration: none;
    font-weight: 600;
    font-size: var(--text-lg);
    transition: all var(--transition-normal);
    box-shadow: var(--shadow-md);
  }

  .cta-button:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg);
  }

  .cta-button i {
    font-size: var(--text-2xl);
  }

  .contact-brosur {
    display: flex;
    flex-direction: column;
  }

  .brosur-header {
    margin-bottom: var(--space-8);
  }

  .brosur-header h3 {
    font-size: var(--text-3xl);
    color: var(--gray-900);
    margin-bottom: var(--space-2);
  }

  .brosur-header p {
    color: var(--gray-600);
    font-size: var(--text-lg);
    margin: 0;
  }

  .brosur-card {
    display: flex;
    flex-direction: column;
    background: var(--white);
    border-radius: var(--radius-2xl);
    overflow: hidden;
    box-shadow: var(--shadow-lg);
    text-decoration: none;
    transition: all var(--transition-normal);
    height: 100%;
  }

  .brosur-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-xl);
  }

  .brosur-preview {
    position: relative;
    width: 100%;
    padding-top: 141.4%;
    overflow: hidden;
  }

  .brosur-preview img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform var(--transition-slow);
  }

  .brosur-card:hover .brosur-preview img {
    transform: scale(1.05);
  }

  .brosur-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: var(--space-3);
    color: var(--white);
    opacity: 0;
    transition: opacity var(--transition-normal);
  }

  .brosur-card:hover .brosur-overlay {
    opacity: 1;
  }

  .brosur-overlay i {
    font-size: var(--text-4xl);
  }

  .brosur-overlay span {
    font-weight: 600;
    font-size: var(--text-lg);
  }

  .brosur-action {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: var(--space-3);
    padding: var(--space-6);
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: var(--white);
  }

  .brosur-action i {
    font-size: var(--text-2xl);
  }

  .brosur-action span {
    font-weight: 600;
    font-size: var(--text-lg);
  }

  .map-section {
    position: relative;
  }

  .map-container {
    border-radius: var(--radius-2xl);
    overflow: hidden;
    box-shadow: var(--shadow-xl);
    border: 4px solid var(--white);
  }

  @media (max-width: 1024px) {
    .contact-content {
      grid-template-columns: 1fr;
      gap: var(--space-10);
    }
  }

  @media (max-width: 768px) {
    .info-header h3,
    .brosur-header h3 {
      font-size: var(--text-2xl);
    }

    .info-header p,
    .brosur-header p {
      font-size: var(--text-base);
    }

    .info-card {
      padding: var(--space-5);
    }

    .card-icon {
      width: 48px;
      height: 48px;
      font-size: var(--text-lg);
    }

    .map-container iframe {
      height: 300px;
    }
  }

  @media (max-width: 640px) {
    .info-card {
      flex-direction: column;
      gap: var(--space-3);
    }

    .card-icon {
      width: 100%;
      height: 48px;
    }

    .cta-button {
      padding: var(--space-4);
    }

    .brosur-action {
      padding: var(--space-5);
    }

    .brosur-action span {
      font-size: var(--text-base);
    }
  }
</style>
