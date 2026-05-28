<script>
  import {
    MessageCircle,
  } from '@lucide/svelte';

  import {
    businessInfo,
  } from '../../data/site.js';
</script>

<a
  href={`https://wa.me/${businessInfo.phone.replace(/\s/g, '')}`}
  target="_blank"
  rel="noopener noreferrer"
  aria-label="WhatsApp"
  class="
    whatsapp-float
    fixed
    bottom-5
    right-5
    z-[999]
    flex
    items-center
    gap-3
    rounded-full
    px-4
    py-3
    text-white
    shadow-[0_18px_50px_rgba(37,211,102,0.35)]
    backdrop-blur-xl
    transition-all
    duration-300
    hover:scale-105
    hover:shadow-[0_24px_65px_rgba(37,211,102,0.45)]
    sm:bottom-6
    sm:right-6
  "
>
  <!-- WAVES -->
  <span class="wave wave-1"></span>

  <span class="wave wave-2"></span>

  <!-- ICON -->
  <span
    class="
      relative
      z-10
      flex
      h-11
      w-11
      items-center
      justify-center
      rounded-full
      bg-white
      text-[#25D366]
      shadow-[0_10px_25px_rgba(0,0,0,0.18)]
    "
  >
    <MessageCircle
      size={22}
      strokeWidth={2.5}
    />
  </span>

  <!-- TEXT -->
  <div
    class="
      relative
      z-10
      hidden
      pr-1
      sm:block
    "
  >
    <span
      class="
        block
        text-[11px]
        font-semibold
        text-white/82
      "
    >
      Escríbenos ahora
    </span>

    <strong
      class="
        block
        text-sm
        font-black
        tracking-wide
      "
    >
      WhatsApp
    </strong>
  </div>
</a>

<style>
  .whatsapp-float {
    position: fixed;

    overflow: hidden;

    background:
      linear-gradient(
        135deg,
        #25d366 0%,
        #1ebe5d 100%
      );
  }

  .wave {
    position: absolute;

    inset: 0;

    border-radius: 999px;

    border:
      2px solid
      rgba(255, 255, 255, 0.45);

    pointer-events: none;
  }

  .wave-1 {
    animation:
      wavePulse 2s infinite ease-out;
  }

  .wave-2 {
    animation:
      wavePulse 2s infinite ease-out;

    animation-delay: 1s;
  }

  @keyframes wavePulse {
    0% {
      opacity: 0.7;

      transform: scale(0.9);
    }

    70% {
      opacity: 0;

      transform: scale(1.6);
    }

    100% {
      opacity: 0;

      transform: scale(1.8);
    }
  }
</style>