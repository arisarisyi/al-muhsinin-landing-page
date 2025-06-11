<script>
// @ts-nocheck

  let formData = {
    name: '',
    email: '',
    phone: '',
    message: '',
    gender: '',
    program: ''
  };
  
  let submitted = false;
  let isLoading = false;
  
  const programs = [
    'Program Tahfidz',
    'Program Kitab Kuning',
    'Program Kewirausahaan',
    'Program Reguler'
  ];
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    isLoading = true;
    
    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 1500));
    
    isLoading = false;
    submitted = true;
    formData = {
      name: '',
      email: '',
      phone: '',
      message: '',
      gender: '',
      program: ''
    };
    
    // Reset submission status after 5 seconds
    setTimeout(() => submitted = false, 5000);
  };
</script>

<section id="contact" class="contact">
  <div class="container">
    <div class="section-title">
      <h2>Hubungi Kami</h2>
    </div>
    
    <div class="contact-content">
      <div class="contact-info">
        <h3>Informasi Kontak</h3>
        <p><i class="fas fa-map-marker-alt"></i> 
          Dsn.Cukir Gang III 02/02 Cukir Diwek Kab. Jombang, Cukir, Kec. Diwek</p>
        <p><i class="fas fa-phone"></i> +62 8123 4439 793</p>
        <!-- <p><i class="fas fa-envelope"></i> info@almuhsinin.com</p> -->
        
        <div class="map-container">
          <iframe title="map"
  width="100%"
  height="300"
  style="border:0;"
  loading="lazy"
  allowfullscreen
  referrerpolicy="no-referrer-when-downgrade"
  src="https://www.google.com/maps?q=-7.616136550143975,112.2371978698461&z=15&output=embed">
</iframe>
        </div>


      </div>
      
      <div class="contact-form">
        <h3>Pendaftaran</h3>
        <a href="./brosur.jpeg" target="_blank" rel="noopener noreferrer">
          <img src="./brosur.jpeg" alt="brosur" width="100%" />
        </a>
      </div>
    </div>
  </div>
</section>

<style>
  .contact {
    background-color: var(--light);
  }
  
  .contact-content {
    display: flex;
    gap: 50px;
  }
  
  .contact-info, .contact-form {
    flex: 1;
  }
  
  .contact-info h3, .contact-form h3 {
    font-size: 1.8rem;
    margin-bottom: 30px;
    color: var(--primary);
  }
  
  .contact-info p {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    color: var(--gray);
  }
  
  .contact-info i {
    margin-right: 15px;
    color: var(--primary);
    font-size: 1.2rem;
    width: 20px;
    text-align: center;
  }
  
  
  .map-container {
    margin-top: 30px;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  }
  
  
  @media (max-width: 992px) {
    .contact-content {
      flex-direction: column;
    }
  
  }
</style>