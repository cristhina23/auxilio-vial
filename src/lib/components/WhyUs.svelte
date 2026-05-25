<script>
  import {
    Headphones,
    Heart,
    ShieldCheck,
    UserRoundCheck,
    Wrench,
  } from '@lucide/svelte';

  import { aboutContent, stats } from '../../data/site.js';

  const statIcons = [UserRoundCheck, Wrench, Heart, Headphones];
</script>

<section
  id="nosotros"
  class="
    whyus-section
    relative
    isolate
    overflow-hidden
    bg-white
    px-4
    py-14
    text-black
    sm:py-16
    lg:min-h-[560px]
  "
>
  <div class="whyus-image-layer absolute inset-y-0 right-0 z-0 hidden w-[58%] lg:block">
    <img
      src="/whyus.png"
      alt="Técnico de auxilio vial atendiendo una emergencia"
      class="h-full w-full object-cover object-center"
    />
  </div>

  <div
    class="
      container-base
      relative
      z-20
      flex
      min-h-full
      flex-col
      gap-8
      lg:min-h-[560px]
      lg:justify-center
      lg:pb-0
    "
  >
    <div class="max-w-[520px]">
      <span class="text-[11px] font-black uppercase text-primary">
        {aboutContent.badge.replace('Â', '')}
      </span>

      <h2
        class="
          mt-4
          font-title
          text-[2.35rem]
          font-black
          leading-[1.04]
          text-black
          sm:text-[3.1rem]
          lg:text-[3.35rem]
        "
      >
        {aboutContent.title.first}
        <br />
        nuestra <span class="text-primary">prioridad</span>
      </h2>

      <p class="mt-6 max-w-[500px] text-sm font-medium leading-7 text-black/68">
        {aboutContent.description}
      </p>
    </div>

    <div class="relative min-h-[320px] overflow-hidden rounded-2xl lg:hidden">
      <img
        src="/whyus.png"
        alt="Técnico de auxilio vial atendiendo una emergencia"
        class="h-full min-h-[320px] w-full object-cover object-center"
      />

      <div class="absolute inset-0 bg-gradient-to-t from-black/35 via-transparent to-white/10"></div>
    </div>

    <div
      class="
        whyus-floating-card
        relative
        z-30
        max-w-[340px]
        rounded-xl
        bg-white
        p-5
        text-black
        shadow-[0_24px_70px_rgba(0,0,0,0.24)]
        lg:absolute
        lg:right-8
        lg:bottom-28
        lg:max-w-[330px]
        lg:p-6
        xl:right-12
      "
    >
      <div class="flex gap-4">
        <span
          class="
            flex
            h-12
            w-12
            shrink-0
            items-center
            justify-center
            rounded-xl
            bg-primary
            text-white
            shadow-[0_14px_34px_rgba(229,9,20,0.28)]
          "
        >
          <ShieldCheck size={25} strokeWidth={2.35} />
        </span>

        <div>
          <h3 class="text-base font-black leading-snug text-black">
            {aboutContent.floatingCard.title}
          </h3>

          <p class="mt-3 text-sm font-medium leading-6 text-black/58">
            {aboutContent.floatingCard.description}
          </p>
        </div>
      </div>
    </div>

    <div
      class="
        whyus-stats
        relative
        z-40
        grid
        grid-cols-2
        gap-3
        sm:max-w-[520px]
        lg:max-w-[520px]
        lg:gap-4
      "
    >
      {#each stats as stat, index}
        {@const Icon = statIcons[index] ?? ShieldCheck}

        <article
          class="
            rounded-xl
            border
            border-black/6
            bg-white/82
            p-4
            shadow-[0_18px_45px_rgba(0,0,0,0.08)]
            backdrop-blur-md
            sm:p-5
          "
        >
          <span
            class="
              flex
              h-10
              w-10
              items-center
              justify-center
              rounded-xl
              border
              border-primary/20
              bg-primary/8
              text-primary
            "
          >
            <Icon size={21} strokeWidth={2.2} />
          </span>

          <strong class="mt-4 block font-title text-3xl font-black leading-none text-black">
            {stat.value}
          </strong>

          <span class="mt-2 block text-[12px] font-semibold leading-4 text-black/55">
            {stat.label}
          </span>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .whyus-section::before {
    content: '';
    position: absolute;
    inset: 0;
    z-index: 10;
    pointer-events: none;
    background:
      radial-gradient(
        circle at 12% 20%,
        rgba(229, 9, 20, 0.06),
        transparent 18rem
      ),
      linear-gradient(
        90deg,
        #ffffff 0%,
        #ffffff 36%,
        rgba(255, 255, 255, 0.92) 42%,
        rgba(255, 255, 255, 0.58) 48%,
        rgba(255, 255, 255, 0.18) 55%,
        rgba(255, 255, 255, 0) 64%
      );
  }

  .whyus-image-layer::after {
    content: '';
    position: absolute;
    inset: 0;
    pointer-events: none;
    background:
      linear-gradient(
        90deg,
        rgba(255, 255, 255, 0.98) 0%,
        rgba(255, 255, 255, 0.7) 16%,
        rgba(255, 255, 255, 0.2) 30%,
        transparent 48%
      ),
      linear-gradient(
        180deg,
        rgba(255, 255, 255, 0.2),
        rgba(0, 0, 0, 0.08)
      );
  }

  .whyus-floating-card {
    border: 1px solid rgba(255, 255, 255, 0.72);
  }

  @media (max-width: 1023px) {
    .whyus-section::before {
      background:
        radial-gradient(
          circle at 20% 10%,
          rgba(229, 9, 20, 0.06),
          transparent 18rem
        );
    }
  }
</style>
