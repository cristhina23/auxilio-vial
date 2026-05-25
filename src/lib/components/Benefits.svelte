<script>
  import { Clock3, MapPin, ShieldCheck, Wrench } from '@lucide/svelte';

  import { features } from '../../data/site.js';

  const icons = [Clock3, MapPin, Wrench, ShieldCheck];
</script>

<section
  class="
    benefits-section
    relative
    z-30
    bg-white
    px-4
    h-40
    
  "
  aria-label="Beneficios"
>
  <div class="container-base relative min-h-[inherit]">
    <div
      class="
        benefits-card
        absolute
        top-[-22px]
        right-4
        left-4
        z-40
        mx-auto
        grid
        max-w-[1180px]
        gap-8
        rounded-lg
        bg-white
        px-7
        py-9
        shadow-card
        sm:top-[-36px]
        sm:grid-cols-2
        sm:px-10
        sm:py-10
        lg:top-[-48px]
        lg:grid-cols-4
        lg:gap-14
        lg:px-16
        lg:py-12
      "
    >
      {#each features as feature, index}
        {@const Icon = icons[index] ?? ShieldCheck}

        <article
          class="
            benefit-item
            flex
            flex-col
            items-start
            gap-3.5
            text-left
            sm:items-start
            sm:text-left
            lg:items-start
            lg:text-left
          "
        >
          <span
            class="
              flex
              h-9
              w-9
              items-center
              justify-center
              rounded-full
              border
              border-primary/25
              bg-primary/8
              text-primary
            "
          >
            <Icon size={18} strokeWidth={2.35} />
          </span>

          <div>
            <h2 class="text-[13px] font-black leading-tight text-black">
              {feature.title}
            </h2>

            <p class="mt-2.5 max-w-[180px] text-[11px] font-medium leading-[1.7] text-black/62">
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
    box-shadow: 0 -1px 0 rgba(255, 255, 255, 0.9);
  }

  .benefits-card {
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(0, 0, 0, 0.06);
  }

  .benefits-card::before {
    content: '';
    position: absolute;
    inset: 0;
    pointer-events: none;
    background:
      linear-gradient(
        180deg,
        rgba(255, 255, 255, 0.9),
        rgba(255, 255, 255, 0)
      ),
      radial-gradient(
        circle at 50% 0%,
        rgba(229, 9, 20, 0.08),
        transparent 34%
      );
  }

  .benefit-item {
    position: relative;
    z-index: 1;
  }
</style>
