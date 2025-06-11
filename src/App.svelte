<script lang="ts">
  import Header from './lib/components/Header.svelte';
  import Hero from './lib/components/Hero.svelte';
  import Activities from './lib/components/Activities.svelte';
  import Facilities from './lib/components/Facilities.svelte';
  import Testimonials from './lib/components/Testimonials.svelte';
  import Contact from './lib/components/Contact.svelte';
  import Footer from './lib/components/Footer.svelte';
  import LogoAnimation from './lib/components/LogoAnimation.svelte';
  import { onMount, onDestroy } from 'svelte';
  import About from './lib/components/About.svelte'

const sections = ['home','about', 'activities', 'facilities', 'testimonials', 'contact'];
  
  let activeSection = 'home';
  
  const scrollTo = (section: string) => {
  activeSection = section;
  const target = document.getElementById(section);
  if (target) {
    target.scrollIntoView({ behavior: 'smooth' });
  }
};

function getCurrentSection(): string {
  const offset = 150; // jarak dari atas viewport untuk mulai dianggap "aktif"
  for (const section of sections) {
    const el = document.getElementById(section);
    if (el) {
      const rect = el.getBoundingClientRect();
      if (rect.top <= offset && rect.bottom >= offset) {
        return section;
      }
    }
  }
  return activeSection; // fallback: tidak berubah
}

function handleScroll() {
  const current = getCurrentSection();
  if (current !== activeSection) {
    activeSection = current;
  }
}

onMount(() => {
  window.addEventListener('scroll', handleScroll, { passive: true });
});

onDestroy(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<svelte:head>
  <title>Pondok Pesantren Kreatif Al-Muhsinin</title>
  <meta name="description" content="Pesantren Modern untuk Mahasiswa Putra dan Putri di Cukir, Diwek Jombang" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
</svelte:head>

<LogoAnimation>
<div class="app">
  <Header {scrollTo} {activeSection} />
  
  <main>
    <Hero id="home" />
    <About id="about" />
    <Activities id="activities" />
    <Facilities id="facilities" />
    <Testimonials id="testimonials" />
    <Contact id="contact" />
  </main>
  
  <Footer />
</div>
</LogoAnimation>