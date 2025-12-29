<script lang="ts">
  const quickLinks = [
    { text: 'Beranda', link: '#home' },
    { text: 'Tentang', link: '#about' },
    { text: 'Kegiatan', link: '#activities' },
    { text: 'Dokumentasi', link: '#facilities' },
    { text: 'Testimoni', link: '#testimonials' },
    { text: 'Kontak', link: '#contact' }
  ];

  const activities = [
    { text: 'Sholat Jamaah', link: '#' },
    { text: 'Pengajian Kitab Kuning', link: '#' },
    { text: '1 Day 1 Juz', link: '#' },
    { text: 'Ilmu Hikmah', link: '#' },
    { text: 'Kewirausahaan', link: '#' }
  ];

  const currentYear = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer-top">
    <div class="container">
      <div class="footer-content">
        <div class="footer-about">
          <div class="logo">
            <img src="/removebg.png" alt="Logo Al-Muhsinin" />
            <span>Al-Muhsinin</span>
          </div>
          <p>Pondok Pesantren Kreatif Al-Muhsinin adalah pesantren modern untuk mahasiswa putra dan putri yang berlokasi di Cukir, Diwek, Jombang.</p>
          <div class="footer-social">
            <a
              href="https://www.facebook.com/almuhsninin"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="Facebook"
              class="social-link facebook"
            >
              <i class="fab fa-facebook-f"></i>
            </a>
            <a
              href="https://www.instagram.com/almuhsinin_cukir"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="Instagram"
              class="social-link instagram"
            >
              <i class="fab fa-instagram"></i>
            </a>
            <a
              href="https://www.youtube.com/@al-muhsininmedia1395"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="YouTube"
              class="social-link youtube"
            >
              <i class="fab fa-youtube"></i>
            </a>
            <a
              href="https://api.whatsapp.com/send/?phone=6281234439793&text&type=phone_number&app_absent=0"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="WhatsApp"
              class="social-link whatsapp"
            >
              <i class="fab fa-whatsapp"></i>
            </a>
          </div>
        </div>

        <div class="footer-links">
          <h4>Tautan Cepat</h4>
          <ul>
            {#each quickLinks as link}
              <li><a href={link.link}>{link.text}</a></li>
            {/each}
          </ul>
        </div>

        <div class="footer-links">
          <h4>Kegiatan</h4>
          <ul>
            {#each activities as activity}
              <li><a href={activity.link}>{activity.text}</a></li>
            {/each}
          </ul>
        </div>

        <div class="footer-contact">
          <h4>Kontak Kami</h4>
          <div class="contact-item">
            <i class="fas fa-map-marker-alt"></i>
            <span>Dsn.Cukir Gang III 02/02, Cukir, Diwek, Jombang</span>
          </div>
          <div class="contact-item">
            <i class="fas fa-phone"></i>
            <span>+62 8123 4439 793</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="footer-bottom">
    <div class="container">
      <div class="footer-bottom-content">
        <p>&copy; {currentYear} Pondok Pesantren Kreatif Al-Muhsinin. All rights reserved.</p>
        <p class="credits">
          Created by <a href="https://alarisyi.web.id" target="_blank" rel="noopener noreferrer">alarisyi</a>
        </p>
      </div>
    </div>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(135deg, var(--gray-900) 0%, var(--gray-800) 100%);
    color: var(--white);
    position: relative;
    overflow: hidden;
  }

  .footer::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary), var(--primary-light), var(--primary));
  }

  .footer-top {
    padding: var(--space-16) 0;
    position: relative;
  }

  .footer-top::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(circle at 20% 50%, rgba(13, 148, 136, 0.05) 0%, transparent 50%),
      radial-gradient(circle at 80% 50%, rgba(13, 148, 136, 0.05) 0%, transparent 50%);
    pointer-events: none;
  }

  .footer-content {
    position: relative;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: var(--space-10);
  }

  .footer-about .logo {
    display: flex;
    align-items: center;
    gap: var(--space-3);
    font-size: var(--text-xl);
    font-weight: 800;
    color: var(--white);
    margin-bottom: var(--space-6);
  }

  .footer-about .logo img {
    height: 50px;
    width: auto;
  }

  .footer-about p {
    color: var(--gray-400);
    line-height: 1.7;
    margin-bottom: var(--space-6);
  }

  .footer-social {
    display: flex;
    gap: var(--space-3);
  }

  .social-link {
    width: 44px;
    height: 44px;
    border-radius: var(--radius-lg);
    background: rgba(255, 255, 255, 0.1);
    color: var(--white);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all var(--transition-normal);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .social-link:hover {
    transform: translateY(-4px);
    border-color: transparent;
  }

  .social-link.facebook:hover {
    background: #1877F2;
    box-shadow: 0 10px 25px -5px rgba(24, 119, 242, 0.5);
  }

  .social-link.instagram:hover {
    background: linear-gradient(45deg, #405DE6, #5851DB, #833AB4, #C13584, #E1306C, #FD1D1D);
    box-shadow: 0 10px 25px -5px rgba(225, 48, 108, 0.5);
  }

  .social-link.youtube:hover {
    background: #FF0000;
    box-shadow: 0 10px 25px -5px rgba(255, 0, 0, 0.5);
  }

  .social-link.whatsapp:hover {
    background: #25D366;
    box-shadow: 0 10px 25px -5px rgba(37, 211, 102, 0.5);
  }

  .footer-links h4,
  .footer-contact h4 {
    font-size: var(--text-lg);
    font-weight: 700;
    margin-bottom: var(--space-6);
    position: relative;
    padding-bottom: var(--space-3);
    color: var(--white);
  }

  .footer-links h4::after,
  .footer-contact h4::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 40px;
    height: 3px;
    background: linear-gradient(90deg, var(--primary), var(--primary-light));
    border-radius: var(--radius-full);
  }

  .footer-links ul {
    list-style: none;
  }

  .footer-links li {
    margin-bottom: var(--space-3);
  }

  .footer-links a {
    color: var(--gray-400);
    text-decoration: none;
    transition: all var(--transition-base);
    display: inline-flex;
    align-items: center;
  }

  .footer-links a:hover {
    color: var(--primary);
    transform: translateX(4px);
  }

  .footer-contact .contact-item {
    display: flex;
    align-items: flex-start;
    gap: var(--space-3);
    margin-bottom: var(--space-4);
    color: var(--gray-400);
  }

  .footer-contact i {
    color: var(--primary);
    font-size: var(--text-lg);
    margin-top: var(--space-1);
    flex-shrink: 0;
  }

  .footer-contact span {
    line-height: 1.6;
  }

  .footer-bottom {
    background: var(--gray-900);
    padding: var(--space-6) 0;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  .footer-bottom-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: var(--space-4);
  }

  .footer-bottom p {
    color: var(--gray-500);
    font-size: var(--text-sm);
    margin: 0;
  }

  .footer-bottom .credits {
    display: flex;
    align-items: center;
    gap: var(--space-2);
  }

  .footer-bottom .credits a {
    color: var(--primary);
    text-decoration: none;
    font-weight: 600;
    transition: color var(--transition-base);
  }

  .footer-bottom .credits a:hover {
    color: var(--primary-light);
  }

  @media (max-width: 1024px) {
    .footer-content {
      grid-template-columns: 1fr 1fr;
      gap: var(--space-8);
    }

    .footer-about {
      grid-column: 1 / -1;
    }
  }

  @media (max-width: 768px) {
    .footer-content {
      grid-template-columns: 1fr;
      gap: var(--space-8);
    }

    .footer-top {
      padding: var(--space-12) 0;
    }

    .footer-bottom-content {
      flex-direction: column;
      text-align: center;
    }
  }

  @media (max-width: 640px) {
    .footer-about .logo {
      font-size: var(--text-lg);
    }

    .footer-about .logo img {
      height: 40px;
    }

    .social-link {
      width: 40px;
      height: 40px;
    }
  }
</style>
