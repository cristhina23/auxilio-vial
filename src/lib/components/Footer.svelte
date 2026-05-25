<script>
  import {
    MessageCircle,
    MapPin,
    Phone,
    Heart,
  } from '@lucide/svelte';
</script>

<footer
  class="
    relative
    overflow-hidden
    border-t
    border-white/5
    bg-black
    px-4
    pt-16
    text-white
  "
>
  <!-- BACKGROUND GLOW -->
  <div
    class="
      absolute
      left-1/2
      top-0
      h-[420px]
      w-[420px]
      -translate-x-1/2
      rounded-full
      bg-primary/10
      blur-[140px]
    "
  />

  <div
    class="
      container-base
      relative
      z-10
    "
  >
    <!-- TOP -->
    <div
      class="
        grid
        gap-12
        border-b
        border-white/6
        pb-12
        md:grid-cols-2
        lg:grid-cols-4
      "
    >
      <!-- BRAND -->
      <div>
        <a
          href="#inicio"
          class="
            inline-flex
            items-center
            gap-3
          "
        >
          <img
            src="/logo.png"
            alt="Rescate Vial Express"
            class="
              h-16
              w-16
              object-contain
            "
          />

          <div>
            <h3
              class="
                font-title
                text-2xl
                font-black
                uppercase
                leading-none
              "
            >
              RESCATE
            </h3>

            <span
              class="
                mt-1
                block
                text-sm
                font-black
                uppercase
                tracking-[0.3em]
                text-primary
              "
            >
              VIAL EXPRESS
            </span>
          </div>
        </a>

        <p
          class="
            mt-5
            max-w-[280px]
            text-sm
            leading-7
            text-white/58
          "
        >
          Brindamos asistencia vial 24/7 en Lima.
          Llegamos rápido para ayudarte cuando
          más lo necesitas.
        </p>
      </div>

      <!-- LINKS -->
      <div>
        <h4
          class="
            text-sm
            font-black
            uppercase
            tracking-[0.2em]
            text-white
          "
        >
          Enlaces
        </h4>

        <div
          class="
            mt-6
            flex
            flex-col
            gap-4
          "
        >
          <a href="#inicio" class="footer-link">
            Inicio
          </a>

          <a href="#servicios" class="footer-link">
            Servicios
          </a>

          <a href="#nosotros" class="footer-link">
            Nosotros
          </a>

          <a href="#cobertura" class="footer-link">
            Cobertura
          </a>

          <a href="#contacto" class="footer-link">
            Contacto
          </a>
        </div>
      </div>

      <!-- SERVICES -->
      <div>
        <h4
          class="
            text-sm
            font-black
            uppercase
            tracking-[0.2em]
            text-white
          "
        >
          Servicios
        </h4>

        <div
          class="
            mt-6
            flex
            flex-col
            gap-4
          "
        >
          <span class="footer-link">
            Paso de corriente
          </span>

          <span class="footer-link">
            Cambio de neumático
          </span>

          <span class="footer-link">
            Inflado de neumáticos
          </span>

          <span class="footer-link">
            Apertura de puertas
          </span>
        </div>
      </div>

      <!-- CONTACT -->
      <div>
        <h4
          class="
            text-sm
            font-black
            uppercase
            tracking-[0.2em]
            text-white
          "
        >
          Contacto
        </h4>

        <div
          class="
            mt-6
            flex
            flex-col
            gap-5
          "
        >
          <div class="contact-item">
            <Phone size={18} />

            <span>932 716 423</span>
          </div>

          <div class="contact-item">
            <MessageCircle size={18} />

            <span>932 716 423</span>
          </div>

          <div class="contact-item">
            <MapPin size={18} />

            <span>Lima, Perú</span>
          </div>
        </div>
      </div>
    </div>

    <!-- BOTTOM -->
    <div
      class="
        flex
        flex-col
        gap-5
        py-6
        text-sm
        text-white/42
        lg:flex-row
        lg:items-center
        lg:justify-between
      "
    >
      <p>
        © 2026 Rescate Vial Express. Todos los
        derechos reservados.
      </p>

      <!-- CC TECH -->
      <a
        href="https://cctechsolutions.dev/en"
        target="_blank"
        rel="noopener noreferrer"
        class="cc-tech"
      >
        <span>
          Hecho con mucho
        </span>

        <span class="heart-wrapper">
          <span class="heart-wave wave-1"></span>

          <span class="heart-wave wave-2"></span>

          <Heart
            size={20}
            class="heart"
            fill="#ff002b"
            color="#ff002b"
            strokeWidth={2.8}
          />
        </span>

        <span>
          por CC Tech Solutions
        </span>
      </a>
    </div>
  </div>
</footer>

<style>
  .footer-link {
    font-size: 0.95rem;

    color: rgba(255, 255, 255, 0.58);

    transition:
      color 0.25s ease,
      transform 0.25s ease;
  }

  .footer-link:hover {
    color: white;

    transform: translateX(4px);
  }

  .contact-item {
    display: flex;

    align-items: center;

    gap: 0.8rem;

    color: rgba(255, 255, 255, 0.68);

    font-size: 0.95rem;
  }

  .cc-tech {
    display: inline-flex;

    align-items: center;

    gap: 0.75rem;

    font-size: 0.95rem;
    font-weight: 700;

    color: rgba(255, 255, 255, 0.72);

    transition:
      color 0.3s ease,
      transform 0.3s ease;
  }

  .cc-tech:hover {
    color: white;

    transform: translateY(-2px);
  }

  .heart-wrapper {
    position: relative;

    display: flex;

    align-items: center;
    justify-content: center;

    width: 34px;
    height: 34px;
  }

  .heart {
    position: relative;

    z-index: 5;

    color: #ff002b;

    transform-origin: center;

    filter:
      drop-shadow(
        0 0 8px rgba(255, 0, 43, 0.95)
      )
      drop-shadow(
        0 0 18px rgba(255, 0, 43, 0.75)
      )
      drop-shadow(
        0 0 36px rgba(255, 0, 43, 0.6)
      );

    animation:
      heartbeat 1s infinite ease-in-out;
  }

  .heart-wave {
    position: absolute;

    inset: 0;

    border-radius: 999px;

    border: 2px solid rgba(255, 0, 43, 0.75);

    animation:
      ripple 2s infinite ease-out;
  }

  .wave-2 {
    animation-delay: 1s;
  }

  @keyframes heartbeat {
    0% {
      transform: scale(1);
    }

    15% {
      transform: scale(1.55);
    }

    30% {
      transform: scale(1);
    }

    45% {
      transform: scale(1.38);
    }

    60% {
      transform: scale(1);
    }

    100% {
      transform: scale(1);
    }
  }

  @keyframes ripple {
    0% {
      opacity: 0.9;

      transform: scale(0.6);
    }

    70% {
      opacity: 0.25;

      transform: scale(2.6);
    }

    100% {
      opacity: 0;

      transform: scale(3.2);
    }
  }
</style>