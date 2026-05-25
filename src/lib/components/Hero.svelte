<script>
  import {
    ArrowRight,
    Clock3,
    MessageCircle,
    Phone,
    UserRoundCheck,
    Zap,
  } from '@lucide/svelte';

  import { heroContent } from '../../data/site.js';

  const [availability, speed, support] = heroContent.stats;
</script>

<section
  id="inicio"
  class="
    hero-section
    relative
    isolate
    min-h-[100svh]
    scroll-mt-28
    overflow-hidden
    bg-black
    pt-22
    text-white
    sm:pt-26
    lg:min-h-[700px]
    lg:pt-22
    xl:pt-26
  " 
>
  <img
    src="/hero.png"
    alt="Grúa de auxilio vial trasladando un auto en carretera"
    class="
      hero-image
      absolute
      inset-0
      -z-20
      h-full
      w-full
      object-cover
    "
  />

  <div class="hero-overlay absolute inset-0 -z-10"></div>

  <div
    class="
      container-base
      relative
      grid
      min-h-[calc(100svh-8rem)]
      items-end
      pb-10
      sm:pb-14
      lg:min-h-[calc(700px-8rem)]
      lg:grid-cols-[minmax(0,560px)_1fr]
      lg:items-center
      lg:pb-12
    "
  >
    <div
      class="
        max-w-[540px]
        pb-[210px]
        sm:pb-[230px]
        md:pb-[250px]
        lg:pb-0
      "
    >
      <div
        class="
          hero-badge
          mb-4
          inline-flex
          items-center
          gap-2
          rounded-full
          px-3
          py-2
          text-[10px]
          font-black
          uppercase
          text-primary
        "
      >
        
        <span>{heroContent.badge}</span>
      </div>

      <h1
        class="
          font-title
          text-[2.25rem]
          font-black
          leading-[1.02]
          tracking-normal
          text-white
          sm:text-[3rem]
          md:text-[3.25rem]
          lg:text-[3.35rem]
          xl:text-[3.65rem]
        "
      >
        {heroContent.title.first}
        <br />
        {heroContent.title.second}
        <br />
        <span class="text-primary">
          {heroContent.title.highlight}
        </span>
      </h1>

      <p
        class="
          mt-5
          max-w-[430px]
          text-sm
          font-medium
          leading-7
          text-white/82
          sm:text-[15px]
        "
      >
        {heroContent.description}
      </p>

      <div
        class="
          mt-7
          grid
          gap-3
          text-[11px]
          font-semibold
          text-white/86
          sm:flex
          sm:flex-wrap
          sm:items-center
          sm:gap-7
        "
      >
        <div class="flex items-center gap-2">
          <span class="flex h-5 w-5 items-center justify-center rounded-full border border-primary/50 text-primary">
            <Clock3 size={12} />
          </span>
          {availability.label}
        </div>

        <div class="flex items-center gap-2">
          <span class="flex h-5 w-5 items-center justify-center rounded-full border border-primary/50 text-primary">
            <Zap size={12} />
          </span>
          {speed.label}
        </div>

        <div class="flex items-center gap-2">
          <span class="flex h-5 w-5 items-center justify-center rounded-full border border-primary/50 text-primary">
            <UserRoundCheck size={12} />
          </span>
          {support.label}
        </div>
      </div>

      <div
        class="
          mt-8
          flex
          flex-col
          gap-3
          sm:flex-row
          sm:items-center
        "
      >
        <a
          href={heroContent.primaryButton.href}
          class="
            hero-button-primary
            inline-flex
            min-h-12
            items-center
            justify-center
            gap-2
            rounded-lg
            px-6
            text-sm
            font-black
            text-white
          "
        >
          <Phone size={15} />
          {heroContent.primaryButton.label}
          <ArrowRight size={15} />
        </a>

        <a
          href={heroContent.secondaryButton.href}
          class="
            inline-flex
            min-h-12
            items-center
            justify-center
            gap-2
            rounded-lg
            border
            border-white/18
            bg-black/45
            px-6
            text-sm
            font-bold
            text-white
            backdrop-blur-md
            transition
            duration-300
            hover:border-white/35
            hover:bg-white/10
          "
        >
          <MessageCircle size={15} />
          {heroContent.secondaryButton.label}
          <MessageCircle size={15} />
        </a>
      </div>
    </div>

    <div
      class="
        hero-glass-card
        absolute
        right-4
        bottom-8
        w-[min(76vw,245px)]
        rounded-xl
        p-5
        text-black
        sm:right-8
        sm:bottom-12
        lg:right-16
        lg:bottom-16
        lg:w-[260px]
      "
    >
      <div class="mb-2 flex items-center gap-2">
        <span class="flex h-7 w-7 items-center justify-center rounded-full bg-primary text-white">
          <Clock3 size={16} strokeWidth={2.6} />
        </span>

        <span class="text-[11px] font-black leading-tight text-black">
          {heroContent.floatingCard.title}
        </span>
      </div>

      <div class="flex items-end gap-2">
        <span class="font-title text-[3.5rem] font-black leading-none text-primary">
          {heroContent.floatingCard.value}
        </span>

        <span class="pb-2 text-2xl font-black leading-none">
          {heroContent.floatingCard.unit}
        </span>
      </div>

      <p class="mt-1 text-sm font-semibold text-black/60">
        {heroContent.floatingCard.description}
      </p>
    </div>
  </div>
</section>

<style>
  .hero-image {
    object-position: 62% center;
  }

  .hero-overlay {
    background:
      radial-gradient(
        circle at 72% 18%,
        rgba(229, 9, 20, 0.38),
        transparent 18rem
      ),
      linear-gradient(
        180deg,
        rgba(0, 0, 0, 0.58) 0%,
        rgba(0, 0, 0, 0.34) 42%,
        rgba(0, 0, 0, 0.9) 100%
      ),
      linear-gradient(
        90deg,
        rgba(0, 0, 0, 0.96) 0%,
        rgba(0, 0, 0, 0.78) 36%,
        rgba(0, 0, 0, 0.26) 74%,
        rgba(0, 0, 0, 0.18) 100%
      );
  }

  .hero-button-primary {
    background: linear-gradient(135deg, #e50914 0%, #ff2a24 100%);
    box-shadow: 0 16px 32px rgba(229, 9, 20, 0.3);
    transition:
      transform 0.28s ease,
      box-shadow 0.28s ease,
      filter 0.28s ease;
  }

  .hero-button-primary:hover {
    filter: saturate(1.12);
    box-shadow: 0 20px 42px rgba(229, 9, 20, 0.42);
    transform: translateY(-2px);
  }

  .hero-badge {
    border: 1px solid rgba(229, 9, 20, 0.42);
    background:
      linear-gradient(
        135deg,
        rgba(229, 9, 20, 0.2),
        rgba(255, 255, 255, 0.055)
      );
    box-shadow:
      0 0 0 1px rgba(255, 255, 255, 0.045) inset,
      0 10px 28px rgba(229, 9, 20, 0.14);
    backdrop-filter: blur(14px) saturate(1.35);
    -webkit-backdrop-filter: blur(14px) saturate(1.35);
  }

  .hero-glass-card {
    overflow: hidden;
    border: 1px solid rgba(255, 255, 255, 0.78);
    background:
      linear-gradient(
        135deg,
        rgba(255, 255, 255, 0.92) 0%,
        rgba(255, 255, 255, 0.72) 48%,
        rgba(255, 255, 255, 0.58) 100%
      );
    box-shadow:
      0 24px 70px rgba(0, 0, 0, 0.34),
      0 0 0 1px rgba(255, 255, 255, 0.38) inset;
    backdrop-filter: blur(20px) saturate(1.45);
    -webkit-backdrop-filter: blur(20px) saturate(1.45);
  }

  .hero-glass-card::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: inherit;
    background:
      radial-gradient(
        circle at 18% 0%,
        rgba(255, 255, 255, 0.9),
        transparent 34%
      ),
      linear-gradient(
        115deg,
        rgba(255, 255, 255, 0.54) 0%,
        transparent 42%
      );
    pointer-events: none;
  }

  .hero-glass-card::after {
    content: '';
    position: absolute;
    top: 10px;
    right: 14px;
    left: 14px;
    height: 1px;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.9),
      transparent
    );
    pointer-events: none;
  }

  .hero-glass-card > * {
    position: relative;
    z-index: 1;
  }

  @media (max-width: 639px) {
    .hero-image {
      object-position: 68% center;
    }
  }

  @media (min-width: 1024px) {
    .hero-image {
      object-position: center;
    }

    .hero-overlay {
      background:
        radial-gradient(
          circle at 76% 20%,
          rgba(229, 9, 20, 0.36),
          transparent 16rem
        ),
        linear-gradient(
          90deg,
          rgba(0, 0, 0, 0.98) 0%,
          rgba(0, 0, 0, 0.9) 30%,
          rgba(0, 0, 0, 0.35) 62%,
          rgba(0, 0, 0, 0.08) 100%
        ),
        linear-gradient(
          180deg,
          rgba(0, 0, 0, 0.16) 0%,
          rgba(0, 0, 0, 0.34) 100%
        );
    }
  }
</style>
