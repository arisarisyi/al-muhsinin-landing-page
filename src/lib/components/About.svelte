<script lang="ts">
</script>

<section id="about" class="hero">
  <div class="container">
    <h1>Tentang</h1>
    <div class="hero-content">
      <div class="hero-text">
        <p class="subtitle">Pondok Pesantren Kreatif Al-Muhsinin adalah pesantren untuk mahasiswa putra dan putri yang berlokasi di Cukir, Diwek, Jombang.</p>
        <p class="subtitle">Pondok Pesantren Kreatif Al-Muhsinin didirikan pada tahun 2014. Pendirian pesantren ini merupakan hasil dari masukan dan dorongan para guru dari KH. Agus Maulana, di antaranya KH. Ishaq Latief dari Tebuireng dan Habib Abu Bakar bin Abbas (Mbah Wo) dari Banyuwangi.
          </p>
          <p class="subtitle">
          KH. Agus Maulana diamanahi untuk mendirikan sebuah pesantren yang menjadi tempat bernaung bagi para mahasiswa yang telah lulus dari Pondok Pesantren Tebuireng, Jombang.
          </p>
          <p class="subtitle">
          Pondok ini kemudian diresmikan oleh Pengasuh Pondok Tebuireng saat itu, KH. Sholahuddin Wahid — putra dari KH. Abdul Wahid Hasyim dan adik dari Gus Dur. Peresmian tersebut turut diiringi dengan doa dan restu dari para masyayikh Tebuireng serta para guru spiritual KH. Agus Maulana.</p>
      </div>
      <div class="hero-image">
        <img src="/gus-sholah.jpg" alt="Gus Sholah" />
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
  padding-top: 120px;
  background: var(--light);
}

.hero-content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 50px; /* Spasi antara teks dan gambar */
}

.hero-text {
  flex: 1;
}

.hero-image {
  flex: 1;
  text-align: center;
}

.hero-image img {
  max-width: 100%;
  border-radius: 10px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 3rem;
  margin-bottom: 20px;
  color: var(--primary);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.subtitle {
  font-size: 1.2rem;
  color: var(--gray);
  margin-bottom: 30px;
}


@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

@media (max-width: 992px) {
  h1 {
    font-size: 2.5rem;
  }
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column; /* Layout vertikal di mobile */
  }

  .hero-text {
    order: 2;
    text-align: center;
    margin-bottom: 20px; /* Jarak antara teks dan gambar */
  }

  .hero-image {
    order: 1;
    margin-top: 20px; /* Jarak antara gambar dan teks */
  }

  .hero-image img {
    max-width: 100%; /* Gambar penuh lebar di mobile */
  }

  .subtitle {
    font-size: 1rem; /* Ukuran font lebih kecil di mobile */
    margin-bottom: 20px; /* Jarak yang lebih pendek */
  }

}

@media (max-width: 576px) {
  h1 {
    font-size: 2rem; /* Ukuran lebih kecil di mobile */
  }

}
</style>