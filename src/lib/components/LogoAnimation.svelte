<script>
  import { onMount } from 'svelte';
  import logoUrl from '../../../static/images/removebg.png';
  import { tweened } from 'svelte/motion';
  import { cubicOut } from 'svelte/easing';
  let show = true;
  let scale = tweened(1, { duration: 1000, easing: cubicOut });
  let rotate = tweened(0, { duration: 1500, easing: cubicOut });

  onMount(() => {
    rotate.set(360); // rotasi satu kali penuh

    setTimeout(() => {
      scale.set(10); // zoom setelah rotasi selesai
    }, 1500);

    setTimeout(() => {
      show = false; // masuk ke halaman utama
    }, 2500);
  });
</script>

{#if show}
  <div class="loading-screen">
    <img src={logoUrl} alt="Logo" style="transform: rotate({$rotate}deg) scale({$scale});" />
  </div>
{:else}
  <slot />
{/if}

<style>
  .loading-screen {
    position: fixed;
    inset: 0;
    background: white;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
    overflow: hidden;
  }

  .loading-screen img {
    width: 150px;
    height: auto;
    transition: transform 0.1s linear;
  }
</style>