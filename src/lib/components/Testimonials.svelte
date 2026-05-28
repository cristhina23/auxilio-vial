<script>
  import {
    ArrowLeft,
    ArrowRight,
    MessageCircle,
    Phone,
    Star,
  } from '@lucide/svelte';

  import { onMount } from 'svelte';

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
        'La atención fue rápida y muy profesional. Me ayudaron inmediatamente.',
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
        'Me quedé sin batería de noche y vinieron sin demora. Muy amables.',
    },

    {
      name: 'Renato G.',
      location: 'San Borja',
      avatar: 'RG',
      review:
        'Excelente comunicación desde el primer momento. Muy confiables.',
    },

    {
      name: 'Lucía T.',
      location: 'Los Olivos',
      avatar: 'LT',
      review:
        'Abrieron mi auto sin dañarlo. Servicio rápido y ordenado.',
    },
  ];

  let start = $state(0);

  let perPage = $state(3);

  const visible = $derived.by(() => {
    return [
      ...reviews.slice(start),
      ...reviews.slice(0, start),
    ].slice(0, perPage);
  });

  const next = () => {
    start =
      (start + 1) % reviews.length;
  };

  const prev = () => {
    start =
      (start - 1 + reviews.length) %
      reviews.length;
  };

  onMount(() => {
    const updatePerPage = () => {
      if (window.innerWidth < 768) {
        perPage = 1;
      } else if (window.innerWidth < 1024) {
        perPage = 2;
      } else {
        perPage = 3;
      }
    };

    updatePerPage();

    window.addEventListener(
      'resize',
      updatePerPage
    );

    return () => {
      window.removeEventListener(
        'resize',
        updatePerPage
      );
    };
  });
</script>

<section
  id="contacto"
  class="
    testimonials-section
    relative
    overflow-visible
    bg-white
    px-4
    pb-20
    pt-12
    text-black
    sm:pt-24
    lg:pb-24
  "
>
  <div
    class="
      container-base
      relative
    "
  >
    <!-- CTA -->
    <div
      class="
        cta-wrapper
        relative
        z-20
        mb-16
        sm:-mt-32
        sm:mb-20
        lg:-mt-36
      "
    >
      <div
        class="
          cta-panel
          grid
          gap-6
          rounded-[28px]
          p-6
          text-white
          shadow-[0_24px_70px_rgba(229,9,20,0.28)]
          sm:p-8
          lg:grid-cols-[1fr_auto]
          lg:items-center
        "
      >
        <!-- LEFT -->
        <div>
          <span
            class="
              text-sm
              font-black
              text-white/82
            "
          >
            ¿Necesitas ayuda ahora?
          </span>

          <h2
            class="
              mt-2
              font-title
              text-[2rem]
              font-black
              leading-tight
              sm:text-4xl
            "
          >
            {ctaContent.title}
          </h2>

          <p
            class="
              mt-3
              max-w-[520px]
              text-sm
              font-semibold
              leading-7
              text-white/82
            "
          >
            {ctaContent.description}
          </p>
        </div>

        <!-- BUTTONS -->
        <div
          class="
            grid
            gap-3
            sm:grid-cols-2
            lg:min-w-[480px]
          "
        >
          <a
            href={ctaContent.primaryButton.href}
            class="
              inline-flex
              min-h-14
              items-center
              justify-center
              gap-3
              rounded-full
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

            <span
              class="
                text-[11px]
                text-primary/60
              "
            >
              Llamar ahora
            </span>
          </a>

          <a
            href={ctaContent.secondaryButton.href}
            class="
              inline-flex
              min-h-14
              items-center
              justify-center
              gap-3
              rounded-full
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
    </div>

    <!-- HEADER -->
    <div
      class="
        flex
        flex-col
        gap-6
        lg:flex-row
        lg:items-end
        lg:justify-between
      "
    >
      <div class="max-w-[720px]">
        <span
          class="
            text-[11px]
            font-black
            uppercase
            text-primary
          "
        >
          Lo que dicen nuestros clientes
        </span>

        <h2
          class="
            mt-4
            font-title
            text-[2rem]
            font-black
            leading-[1.08]
            sm:text-[2.7rem]
          "
        >
          Historias reales de personas que
          <span class="text-primary">
            confían en nosotros
          </span>
        </h2>
      </div>

      <!-- DESKTOP NAV -->
      <div
        class="
          hidden
          gap-3
          lg:flex
        "
      >
        <button
          type="button"
          class="review-nav"
          onclick={prev}
        >
          <ArrowLeft size={20} />
        </button>

        <button
          type="button"
          class="review-nav"
          onclick={next}
        >
          <ArrowRight size={20} />
        </button>
      </div>
    </div>

    <!-- REVIEWS -->
    <div
      class="
        mt-10
        grid
        gap-5
        md:grid-cols-2
        lg:grid-cols-3
      "
    >
      {#each visible as item}
        <article
          class="
            review-card
            rounded-[24px]
            bg-white
            p-6
            animate-review
          "
        >
          <!-- STARS -->
          <div
            class="
              flex
              gap-1
              text-primary
            "
          >
            {#each [1,2,3,4,5] as _}
              <Star
                size={16}
                fill="currentColor"
              />
            {/each}
          </div>

          <!-- REVIEW -->
          <p
            class="
              mt-5
              text-sm
              font-medium
              leading-7
              text-black/68
            "
          >
            “{item.review}”
          </p>

          <!-- USER -->
          <div
            class="
              mt-6
              flex
              items-center
              gap-3
            "
          >
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
              <strong
                class="
                  block
                  text-sm
                  font-black
                  text-black
                "
              >
                {item.name}
              </strong>

              <span
                class="
                  text-xs
                  font-semibold
                  text-black/45
                "
              >
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
      linear-gradient(
        135deg,
        #b80710 0%,
        #e50914 58%,
        #ff1f29 100%
      );
  }

  .review-card {
    border:
      1px solid rgba(0, 0, 0, 0.045);

    box-shadow:
      0 18px 55px
      rgba(0, 0, 0, 0.08);

    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .review-card:hover {
    transform: translateY(-6px);

    box-shadow:
      0 24px 70px
      rgba(0, 0, 0, 0.12);
  }

  .review-nav {
    display: inline-flex;

    width: 46px;
    height: 46px;

    align-items: center;
    justify-content: center;

    border-radius: 12px;

    background: #e50914;

    color: white;

    transition:
      transform 0.25s ease,
      background 0.25s ease,
      box-shadow 0.25s ease;
  }

  .review-nav:hover {
    background: #ff1f29;

    transform: translateY(-2px);

    box-shadow:
      0 12px 28px
      rgba(229, 9, 20, 0.28);
  }

  .review-nav:active {
    transform: scale(0.92);
  }

  .animate-review {
    animation:
      reviewIn 0.4s ease;
  }

  @keyframes reviewIn {
    from {
      opacity: 0;

      transform:
        translateY(20px)
        scale(0.96);
    }

    to {
      opacity: 1;

      transform:
        translateY(0)
        scale(1);
    }
  }
</style>