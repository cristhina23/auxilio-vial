<script>
  import {
    Clock3,
    MapPin,
    ShieldCheck,
    Wrench,
  } from '@lucide/svelte';

  import { features } from '../../data/site.js';

  const icons = [
    Clock3,
    MapPin,
    Wrench,
    ShieldCheck,
  ];
</script>

<section
  class="
    benefits-section
    relative
    z-30
    bg-white
    px-4
    pt-10
    pb-14
    sm:pt-28
    sm:pb-16
    lg:pt-32
    lg:pb-20
  "
  aria-label="Beneficios"
>
  <div
    class="
      container-base
      relative
    "
  >
    <!-- FLOATING CARD -->
    <div
      class="
        benefits-card
        relative
        z-40
        grid
        w-full
        gap-8
        rounded-[28px]
        bg-white
        px-7
        py-9
        shadow-[0_20px_50px_rgba(0,0,0,0.10)]
        sm:-mt-24
        sm:grid-cols-2
        sm:px-10
        sm:py-10
        sm:shadow-[0_30px_90px_rgba(0,0,0,0.16)]
        lg:-mt-48
        lg:grid-cols-4
        lg:gap-14
        lg:px-14
        lg:py-12
      "
    >
      {#each features as feature, index}
        {@const Icon =
          icons[index] ?? ShieldCheck}

        <article
          class="
            benefit-item
            flex
            flex-col
            items-start
            gap-4
            text-left
          "
        >
          <!-- ICON -->
          <span
            class="
              flex
              h-12
              w-12
              items-center
              justify-center
              rounded-2xl
              border
              border-primary/12
              bg-primary/5
              text-primary
              shadow-[0_10px_25px_rgba(229,9,20,0.08)]
            "
          >
            <Icon
              size={20}
              strokeWidth={2.3}
            />
          </span>

          <!-- CONTENT -->
          <div>
            <h2
              class="
                text-[15px]
                font-black
                leading-tight
                text-black
              "
            >
              {feature.title}
            </h2>

            <p
              class="
                mt-3
                max-w-[220px]
                text-[12px]
                font-medium
                leading-[1.8]
                text-black/58
              "
            >
              {feature.description}
            </p>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .benefits-section {
    position: relative;

    overflow: visible;
  }

  .benefits-card {
    position: relative;

    overflow: hidden;

    border:
      1px solid rgba(0, 0, 0, 0.05);

    backdrop-filter: blur(18px);
  }

  .benefits-card::before {
    content: '';

    position: absolute;

    inset: 0;

    pointer-events: none;

    background:
      linear-gradient(
        180deg,
        rgba(255, 255, 255, 0.95),
        rgba(255, 255, 255, 0)
      ),
      radial-gradient(
        circle at 50% 0%,
        rgba(229, 9, 20, 0.07),
        transparent 36%
      );
  }

  .benefit-item {
    position: relative;

    z-index: 2;
  }
</style>