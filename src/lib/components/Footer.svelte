<script>
  const quickLinks = [
    { text: 'Beranda', link: '#home' },
    { text: 'Tentang', link: '#about' },
    { text: 'Kegiatan', link: '#activities' },
    { text: 'Dokumentasi Kegiatan', link: '#facilities' },
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
</script>

<footer class="footer">
  <div class="container">
    <div class="footer-content">
      <div class="footer-about">
        <div class="logo">
          <img src="./static/images/removebg.png" alt="Logo Al-Muhsinin" />
          <span>Al-Muhsinin</span>
        </div>
        <p>Pondok Pesantren Kreatif Al-Muhsinin adalah pesantren modern untuk mahasiswa putra dan putri yang berlokasi di Cukir, Diwek, Jombang.</p>
        <div class="footer-social">
          <a href="https://www.facebook.com/almuhsninin" target="_blank" aria-label="fb"><i class="fab fa-facebook-f"></i></a>
          <a href="https://www.instagram.com/almuhsinin_cukir" target="_blank" aria-label="ig"><i class="fab fa-instagram"></i></a>
          <a href="https://www.youtube.com/@al-muhsininmedia1395" target="_blank" aria-label="yt"><i class="fab fa-youtube"></i></a>
          <a href="https://api.whatsapp.com/send/?phone=6281234439793&text&type=phone_number&app_absent=0" target="_blank" aria-label="wa"><i class="fab fa-whatsapp"></i></a>
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
        <p><i class="fas fa-map-marker-alt"></i> Dsn.Cukir Gang III 02/02 Cukir Diwek Kab. Jombang, Cukir, Kec. Diwek</p>
        <p><i class="fas fa-phone"></i> +62 8123 4439 793</p>
        <!-- <p><i class="fas fa-envelope"></i> info@almuhsinin.com</p> -->
      </div>
    </div>
    
    <div class="footer-bottom">
      <p>&copy; {new Date().getFullYear()} Pondok Pesantren Kreatif Al-Muhsinin. All Rights Reserved. Created by: <a href="https://alarisyi.web.id" target="_blank" rel="noopener noreferrer">alarisyi</a></p>
    </div>
  </div>
</footer>

<style>
  .footer {
    background-color: var(--dark);
    color: white;
    padding: 60px 0 0;
  }

  a{
    color: white;
    text-decoration: none;
    cursor: pointer;
  }
  
  .footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 40px;
    margin-bottom: 40px;
  }
  
  .footer-about .logo {
    display: flex;
    align-items: center;
    font-size: 1.5rem;
    font-weight: 700;
    color: white;
    margin-bottom: 20px;
  }
  
  .footer-about .logo img {
    height: 40px;
    margin-right: 10px;
  }
  
  .footer-about p {
    margin-bottom: 20px;
    color: rgba(255, 255, 255, 0.7);
  }
  
  .footer-social {
    display: flex;
    gap: 15px;
  }
  
  .footer-social a {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: rgba(255, 255, 255, 0.1);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    transition: all 0.3s ease;
  }
  
  .footer-social a:hover {
    background-color: var(--primary);
    transform: translateY(-3px);
  }
  
  .footer-links h4, .footer-contact h4 {
    font-size: 1.2rem;
    margin-bottom: 20px;
    position: relative;
    padding-bottom: 10px;
  }
  
  .footer-links h4::after, .footer-contact h4::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 50px;
    height: 2px;
    background-color: var(--primary);
  }
  
  .footer-links ul {
    list-style: none;
  }
  
  .footer-links li {
    margin-bottom: 10px;
  }
  
  .footer-links a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color 0.3s ease;
  }
  
  .footer-links a:hover {
    color: var(--primary);
  }
  
  .footer-contact p {
    display: flex;
    align-items: center;
    margin-bottom: 15px;
    color: rgba(255, 255, 255, 0.7);
  }
  
  .footer-contact i {
    margin-right: 15px;
    color: var(--primary);
    font-size: 1rem;
    width: 20px;
    text-align: center;
  }
  
  .footer-bottom {
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    padding-top: 20px;
    text-align: center;
    color: rgba(255, 255, 255, 0.5);
    font-size: 0.9rem;
  }
  
  @media (max-width: 768px) {
    .footer-content {
      grid-template-columns: 1fr;
    }
  }
</style>