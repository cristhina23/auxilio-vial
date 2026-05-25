<script>
  import { BatteryCharging, KeyRound, LifeBuoy, Wind } from '@lucide/svelte';

  import { services } from '../../data/site.js';

  const icons = [BatteryCharging, LifeBuoy, Wind, KeyRound];
</script>

<section
  id="servicios"
  class="
    services-section
    relative
    z-10
    overflow-hidden
    bg-black
    px-4
    pb-20
    pt-28
    text-white
    sm:pt-32
    lg:pt-36
  "
>
  <div class="container-base relative z-10">
    <div
      class="
        max-w-[800px]
      "
    >
      <div>
        <span class="text-[11px] font-black uppercase text-primary">
          Nuestros servicios
        </span>

        <h2
          class="
            mt-3
            
            font-title
            text-[2rem]
            font-black
            leading-[1.05]
            text-white
            sm:text-[2.55rem]
          "
        >
          Soluciones para cada situación
        </h2>

        <span class="mt-5 block h-[3px] w-10 rounded-full bg-primary"></span>
      </div>

      <p class="mt-6  text-sm font-medium leading-7 text-white/72">
        Nos encargamos de todo para que tú no tengas que preocuparte.
      </p>
    </div>

    <div class="mt-9 grid gap-5 sm:grid-cols-2 lg:grid-cols-4">
      {#each services as service, index}
        {@const Icon = icons[index] ?? LifeBuoy}

        <article
          class="
            service-card
            group
            overflow-hidden
            rounded-lg
            border
            border-white/10
            bg-white/[0.035]
          "
        >
          <div class="relative h-[190px] overflow-hidden">
            <img
              src={`/${service.image}`}
              alt={service.title}
              class="
                h-full
                w-full
                object-cover
                transition
                duration-500
                group-hover:scale-105
              "
            />

            <div class="absolute inset-0 bg-gradient-to-t from-black via-black/38 to-transparent"></div>
          </div>

          <div class="relative px-5 pb-5 pt-0">
            <span
              class="
                -mt-8
                mb-4
                flex
                h-10
                w-10
                items-center
                justify-center
                rounded-md
                bg-primary
                text-white
                shadow-[0_10px_28px_rgba(229,9,20,0.34)]
              "
            >
              <Icon size={20} strokeWidth={2.35} />
            </span>

            <h3 class="text-[15px] font-black leading-tight text-white">
              {service.title}
            </h3>

            <p class="mt-3 text-[13px] font-medium leading-6 text-white/66">
              {service.description}
            </p>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .services-section::before {
    content: '';
    position: absolute;
    inset: 0;
    pointer-events: none;
    background:
      radial-gradient(
        circle at 82% 8%,
        rgba(229, 9, 20, 0.16),
        transparent 20rem
      ),
      linear-gradient(
        180deg,
        rgba(255, 255, 255, 0.02),
        rgba(0, 0, 0, 0) 26%
      );
  }

  .service-card {
    box-shadow: 0 18px 50px rgba(0, 0, 0, 0.2);
    transition:
      border-color 0.3s ease,
      background-color 0.3s ease,
      transform 0.3s ease;
  }

  .service-card:hover {
    border-color: rgba(229, 9, 20, 0.34);
    background-color: rgba(255, 255, 255, 0.055);
    transform: translateY(-4px);
  }
</style>
