<script lang="ts">
  import Header from '../components/Header.svelte';
  import Hero from '../components/Hero.svelte';
  import Activities from '../components/Activities.svelte';
  import Facilities from '../components/Facilities.svelte';
  import Testimonials from '../components/Testimonials.svelte';
  import Contact from '../components/Contact.svelte';
  import Footer from '../components/Footer.svelte';
  import LogoAnimation from '../components/LogoAnimation.svelte';
  import About from '../components/About.svelte';
  import { onMount, onDestroy } from 'svelte';

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
    const offset = 150;
    for (const section of sections) {
      const el = document.getElementById(section);
      if (el) {
        const rect = el.getBoundingClientRect();
        if (rect.top <= offset && rect.bottom >= offset) {
          return section;
        }
      }
    }
    return activeSection;
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
