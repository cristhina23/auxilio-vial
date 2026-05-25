<script>
  import { CheckCircle2, MapPin, PhoneCall, Truck, Wrench } from '@lucide/svelte';

  import { coverageZones, processSteps } from '../../data/site.js';

  const stepIcons = [PhoneCall, Truck, Wrench, CheckCircle2];
</script>

<section
  id="cobertura"
  class="
    process-section
    relative
    isolate
    overflow-hidden
    bg-black
    px-4
    py-16
    text-white
    sm:py-20
    lg:py-24
  "
>
  <div class="container-base relative z-10">
    <div class="mx-auto max-w-[420px] text-center">
      <span class="text-[11px] font-black uppercase text-primary">
        ¿Cómo funciona?
      </span>

      <h2
        class="
          mt-4
          font-title
          text-[2.35rem]
          font-black
          leading-[1.05]
          text-white
          sm:text-[3rem]
        "
      >
        Así de fácil
      </h2>

      <span class="mx-auto mt-5 block h-[3px] w-10 rounded-full bg-primary"></span>
    </div>

    <div
      class="
        process-steps
        mx-auto
        mt-12
        grid
        w-full
        max-w-[1080px]
        gap-8
        sm:grid-cols-2
        lg:grid-cols-4
        lg:gap-10
      "
    >
      {#each processSteps as item, index}
        {@const Icon = stepIcons[index] ?? CheckCircle2}

        <article class="process-step relative flex flex-col items-center text-center">
          <div
            class="
              process-icon
              flex
              h-20
              w-20
              items-center
              justify-center
              rounded-full
              border
              border-white/8
              bg-white/[0.03]
              text-white/84
              shadow-[0_18px_60px_rgba(0,0,0,0.32)]
              backdrop-blur-sm
            "
          >
            <Icon size={35} strokeWidth={1.8} />
          </div>

          <span
            class="
              mt-4
              flex
              h-7
              w-7
              items-center
              justify-center
              rounded-full
              bg-primary
              text-[12px]
              font-black
              text-white
              shadow-[0_10px_24px_rgba(229,9,20,0.36)]
              lg:absolute
              lg:left-1/2
              lg:top-[78px]
              lg:mt-0
              lg:-translate-x-[40px]
            "
          >
            {index + 1}
          </span>

          <div class="mt-3 lg:mt-10">
            <h3 class="text-base font-black text-white">
              {item.title}
            </h3>

            <p class="mx-auto mt-3 max-w-[190px] text-sm font-medium leading-6 text-white/55">
              {item.description}
            </p>
          </div>
        </article>
      {/each}
    </div>

    <div
      class="
        coverage-card
        mt-14
        grid
        gap-7
        rounded-2xl
        border
        border-white/8
        bg-white/[0.035]
        p-6
        backdrop-blur-sm
        sm:p-8
        lg:grid-cols-[270px_1fr]
        lg:items-start
      "
    >
      <div>
        <span class="text-[11px] font-black uppercase text-primary">
          Cobertura
        </span>

        <h3 class="mt-3 font-title text-3xl font-black leading-tight text-white">
          Llegamos a tu zona
        </h3>

        <p class="mt-4 text-sm font-medium leading-7 text-white/58">
          Atendemos emergencias vehiculares en estos distritos y zonas cercanas.
        </p>
      </div>

      <div class="flex flex-wrap gap-3">
        {#each coverageZones as zone}
          <span
            class="
              inline-flex
              items-center
              gap-2
              rounded-full
              border
              border-white/10
              bg-black/35
              px-4
              py-2.5
              text-sm
              font-semibold
              text-white/78
            "
          >
            <MapPin size={15} class="text-primary" />
            {zone}
          </span>
        {/each}
      </div>
    </div>
  </div>
</section>

<style>
  .process-section::before {
    content: '';
    position: absolute;
    inset: 0;
    z-index: -1;
    background:
      radial-gradient(
        circle at 12% 20%,
        rgba(229, 9, 20, 0.13),
        transparent 20rem
      ),
      radial-gradient(
        circle at 80% 10%,
        rgba(255, 255, 255, 0.06),
        transparent 22rem
      ),
      linear-gradient(180deg, #070707, #0b0b0b 48%, #050505);
  }

  .process-step::after {
    content: '';
    display: none;
  }

  .coverage-card {
    box-shadow: 0 24px 80px rgba(0, 0, 0, 0.28);
  }

  @media (min-width: 1024px) {
    .process-step:not(:last-child)::after {
      display: block;
      position: absolute;
      top: 39px;
      left: calc(50% + 56px);
      width: calc(100% - 112px);
      height: 1px;
      background: linear-gradient(
        90deg,
        rgba(255, 255, 255, 0.28),
        rgba(255, 255, 255, 0.05)
      );
    }

    .process-step:not(:last-child)::before {
      content: '';
      position: absolute;
      top: 37px;
      right: -5px;
      z-index: 1;
      width: 5px;
      height: 5px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.72);
      box-shadow: 0 0 16px rgba(255, 255, 255, 0.45);
    }
  }
</style>
