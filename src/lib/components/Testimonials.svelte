<script>
  import { ArrowLeft, ArrowRight, MessageCircle, Phone, Star } from '@lucide/svelte';

  import { ctaContent } from '../../data/site.js';

  const reviews = [
    {
      name: 'Carlos M.',
      location: 'Surco',
      avatar: 'CM',
      review:
        'Excelente servicio, llegaron súper rápido cuando se me pinchó la llanta. Muy recomendados.',
    },
    {
      name: 'Andrea R.',
      location: 'San Miguel',
      avatar: 'AR',
      review:
        'Tuve un accidente y me ayudaron con la grúa de inmediato. Muy profesionales y atentos.',
    },
    {
      name: 'Jorge L.',
      location: 'La Molina',
      avatar: 'JL',
      review:
        'Se me acabó la gasolina y en menos de 30 minutos ya estaba de vuelta en camino.',
    },
    {
      name: 'María P.',
      location: 'Miraflores',
      avatar: 'MP',
      review:
        'Me quedé sin batería de noche y vinieron sin demora. El técnico fue muy amable.',
    },
    {
      name: 'Renato G.',
      location: 'San Borja',
      avatar: 'RG',
      review:
        'Atención clara desde el primer mensaje. Llegaron a tiempo y solucionaron todo rápido.',
    },
    {
      name: 'Lucía T.',
      location: 'Los Olivos',
      avatar: 'LT',
      review:
        'Necesitaba abrir mi auto y no dañaron nada. Servicio ordenado y confiable.',
    },
  ];
</script>

<section
  id="contacto"
  class="
    testimonials-section
    relative
    bg-white
    px-4
    pb-20
    pt-0
    text-black
    lg:pb-24
  "
>
  <div class="container-base">
    <div
      class="
        cta-panel
        absolute
        z-20
        -mt-12
        grid
        gap-6
        rounded-xl
        bg-primary
        p-6
        text-white
        shadow-[0_24px_70px_rgba(229,9,20,0.28)]
        sm:p-8
        lg:grid-cols-[1fr_auto]
        lg:items-center
      "
    >
      <div>
        <span class="text-sm font-black text-white/82">
          ¿Necesitas ayuda ahora?
        </span>

        <h2 class="mt-2 font-title text-3xl font-black leading-tight sm:text-4xl">
          {ctaContent.title}
        </h2>

        <p class="mt-3 text-sm font-semibold text-white/82">
          {ctaContent.description}
        </p>
      </div>

      <div class="grid gap-3 sm:grid-cols-2 lg:min-w-[480px]">
        <a
          href={ctaContent.primaryButton.href}
          class="
            inline-flex
            min-h-14
            items-center
            justify-center
            gap-3
            rounded-lg
            bg-white
            px-5
            text-sm
            font-black
            text-primary
            shadow-[0_16px_40px_rgba(0,0,0,0.16)]
          "
        >
          <Phone size={18} />
          {ctaContent.primaryButton.label}
          <span class="text-[11px] text-primary/60">Llamar ahora</span>
        </a>

        <a
          href={ctaContent.secondaryButton.href}
          class="
            inline-flex
            min-h-14
            items-center
            justify-center
            gap-3
            rounded-lg
            border
            border-white/35
            px-5
            text-sm
            font-black
            text-white
            transition
            duration-300
            hover:bg-white/10
          "
        >
          <MessageCircle size={18} />
          {ctaContent.secondaryButton.label}
         
        </a>
      </div>
    </div>

    <div class="mt-26 flex flex-col pt-20 gap-6 lg:mt-20 lg:flex-row lg:items-end lg:justify-between">
      <div class="max-w-[520px]">
        <span class="text-[11px] font-black uppercase text-primary">
          Lo que dicen nuestros clientes
        </span>

        <h2 class="mt-4 font-title text-[2rem] font-black leading-[1.08] sm:text-[2.7rem]">
          Historias reales de personas que
          <span class="text-primary"> confiaron en nosotros</span>
        </h2>
      </div>

      <div class="hidden gap-3 lg:flex">
        <button class="review-nav" aria-label="Anterior">
          <ArrowLeft size={20} />
        </button>

        <button class="review-nav" aria-label="Siguiente">
          <ArrowRight size={20} />
        </button>
      </div>
    </div>

    <div class="mt-9 grid gap-5 md:grid-cols-2 xl:grid-cols-3">
      {#each reviews as item}
        <article
          class="
            review-card
            rounded-xl
            bg-white
            p-6
            shadow-[0_18px_55px_rgba(0,0,0,0.08)]
          "
        >
          <div class="flex gap-1 text-primary">
            {#each Array(5) as _}
              <Star size={16} fill="currentColor" />
            {/each}
          </div>

          <p class="mt-5 text-sm font-medium leading-7 text-black/68">
            “{item.review}”
          </p>

          <div class="mt-6 flex items-center gap-3">
            <span
              class="
                flex
                h-11
                w-11
                items-center
                justify-center
                rounded-full
                bg-black
                text-xs
                font-black
                text-white
              "
            >
              {item.avatar}
            </span>

            <div>
              <strong class="block text-sm font-black text-black">
                {item.name}
              </strong>

              <span class="text-xs font-semibold text-black/45">
                {item.location}
              </span>
            </div>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .testimonials-section {
    background:
      radial-gradient(
        circle at 14% 24%,
        rgba(229, 9, 20, 0.06),
        transparent 24rem
      ),
      #ffffff;
  }

  .cta-panel {
    background:
      radial-gradient(
        circle at 82% 20%,
        rgba(255, 255, 255, 0.18),
        transparent 15rem
      ),
      linear-gradient(135deg, #b80710 0%, #e50914 58%, #ff1f29 100%);
  }

  .review-card {
    border: 1px solid rgba(0, 0, 0, 0.045);
  }

  .review-nav {
    display: inline-flex;
    width: 42px;
    height: 42px;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
    background: #e50914;
    color: #ffffff;
    transition:
      transform 0.25s ease,
      background 0.25s ease;
  }

  .review-nav:hover {
    background: #ff1f29;
    transform: translateY(-2px);
  }
</style>
