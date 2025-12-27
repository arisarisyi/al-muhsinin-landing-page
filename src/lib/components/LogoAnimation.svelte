<script lang="ts">
  import { onMount } from 'svelte';
  import { quintOut } from 'svelte/easing';
  import logoUrl from '/removebg.png';

  interface LoadingState {
    isLoading: boolean;
    progress: number;
    logoVisible: boolean;
    fadeOut: boolean;
  }

  let state: LoadingState = {
    isLoading: true,
    progress: 0,
    logoVisible: true,
    fadeOut: false
  };

  let contentOpacity = 0;
  let logoScale = 1;
  let logoRotate = 0;

  onMount(() => {
    // Animasi progress bar
    const progressInterval = setInterval(() => {
      if (state.progress < 100) {
        state.progress += Math.random() * 15 + 5;
        if (state.progress > 100) state.progress = 100;
      }
    }, 150);

    // Animasi logo rotate dan scale
    setTimeout(() => {
      logoRotate = 360;
    }, 300);

    setTimeout(() => {
      logoScale = 1.2;
    }, 800);

    // Mulai fade out loading screen
    setTimeout(() => {
      state.fadeOut = true;
      clearInterval(progressInterval);
    }, 2000);

    // Transition ke konten utama
    setTimeout(() => {
      state.isLoading = false;
      contentOpacity = 1;
    }, 2800);
  });
</script>

{#if state.isLoading}
  <div class="loading-screen" class:fade-out={state.fadeOut}>
    <div class="loading-content">
      <div class="logo-container" style="transform: scale({logoScale}) rotate({logoRotate}deg);">
        <img src={logoUrl} alt="Pondok Pesantren Kreatif Al-Muhsinin" />
      </div>

      <div class="text-container">
        <h1 class="title">Pondok Pesantren Kreatif</h1>
        <p class="subtitle">Al-Muhsinin</p>
      </div>

      <div class="progress-container">
        <div class="progress-bar">
          <div class="progress-fill" style="width: {state.progress}%"></div>
        </div>
        <p class="progress-text">{Math.floor(state.progress)}%</p>
      </div>

      <div class="dots-container">
        <span class="dot" style="--delay: 0s;"></span>
        <span class="dot" style="--delay: 0.2s;"></span>
        <span class="dot" style="--delay: 0.4s;"></span>
      </div>
    </div>

    <div class="pattern-bg"></div>
  </div>
{:else}
  <div style="opacity: {contentOpacity}; transition: opacity 0.8s ease-out;">
    <slot />
  </div>
{/if}

<style>
  .loading-screen {
    position: fixed;
    inset: 0;
    background: linear-gradient(135deg, #0d9488 0%, #0f766e 50%, #115e59 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
    transition: opacity 0.8s ease-out, visibility 0.8s ease-out;
  }

  .loading-screen.fade-out {
    opacity: 0;
    visibility: hidden;
  }

  .loading-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    z-index: 1;
  }

  .logo-container {
    transition: transform 1.2s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  .logo-container img {
    width: 120px;
    height: auto;
    filter: drop-shadow(0 20px 40px rgba(0, 0, 0, 0.3));
  }

  .text-container {
    text-align: center;
    color: white;
    animation: fadeInUp 0.8s ease-out 0.3s both;
  }

  .title {
    font-size: 1.5rem;
    font-weight: 700;
    margin: 0;
    letter-spacing: 0.05em;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  }

  .subtitle {
    font-size: 1.25rem;
    font-weight: 500;
    margin: 0.5rem 0 0 0;
    opacity: 0.95;
    letter-spacing: 0.1em;
  }

  .progress-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
    width: 200px;
    animation: fadeInUp 0.8s ease-out 0.6s both;
  }

  .progress-bar {
    width: 100%;
    height: 4px;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 10px;
    overflow: hidden;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #fbbf24, #f59e0b);
    border-radius: 10px;
    transition: width 0.3s ease-out;
    box-shadow: 0 0 10px rgba(251, 191, 36, 0.5);
  }

  .progress-text {
    color: white;
    font-size: 0.875rem;
    font-weight: 600;
    margin: 0;
    letter-spacing: 0.05em;
  }

  .dots-container {
    display: flex;
    gap: 0.5rem;
    animation: fadeInUp 0.8s ease-out 0.9s both;
  }

  .dot {
    width: 8px;
    height: 8px;
    background: rgba(255, 255, 255, 0.6);
    border-radius: 50%;
    animation: pulse 1.4s ease-in-out infinite;
    animation-delay: var(--delay);
  }

  .pattern-bg {
    position: absolute;
    inset: 0;
    opacity: 0.05;
    background-image:
      radial-gradient(circle at 25% 25%, white 2%, transparent 2%),
      radial-gradient(circle at 75% 75%, white 2%, transparent 2%);
    background-size: 30px 30px;
    pointer-events: none;
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes pulse {
    0%, 80%, 100% {
      transform: scale(0.8);
      opacity: 0.5;
    }
    40% {
      transform: scale(1.2);
      opacity: 1;
    }
  }

  @media (max-width: 640px) {
    .logo-container img {
      width: 100px;
    }

    .title {
      font-size: 1.25rem;
    }

    .subtitle {
      font-size: 1rem;
    }

    .progress-container {
      width: 160px;
    }
  }
</style>