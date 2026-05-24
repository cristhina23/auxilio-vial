<script>
  import { Menu, X, Phone } from '@lucide/svelte';

  import {
    businessInfo,
    navigationLinks,
  } from '../../data/site.js';

  let isMenuOpen = $state(false);

  const toggleMenu = () => {
    isMenuOpen = !isMenuOpen;
  };

  const closeMenu = () => {
    isMenuOpen = false;
  };
</script>

<header
  class="
    fixed
    top-4
    left-0
    z-50
    w-full
    px-4
  "
>
  <nav
    class="
      container-base
      flex
      h-[64px]
      items-center
      justify-between
      rounded-2xl
      border
      border-white/5
      bg-black/80
      px-4
      backdrop-blur-xl
      shadow-[0_0_40px_rgba(0,0,0,0.35)]
      lg:px-6
    "
  >
    <!-- LOGO -->
    <a
      href="#inicio"
      class="
        flex
        items-center
        gap-3
        shrink-0
      "
    >
      <!-- ICON -->
      <div
        class="
          flex
          h-14
          w-12
          items-center
          justify-center
          overflow-hidden
          rounded-xl
          border
          border-red-500/20
          bg-black
          shadow-[0_0_20px_rgba(229,9,20,0.15)]
        "
      >
        <img
          src="logo.png"
          alt={businessInfo.name}
          class="
            h-14
            w-14
            object-contain
          "
        />
      </div>

      <!-- TEXT -->
      <div
        class="
          flex
          flex-col
          leading-none
        "
      >
        <span
          class="
            font-title
            text-[1.05rem]
            font-black
            uppercase
            tracking-tight
            text-white
          "
        >
          AUXILIO
        </span>

        <span
          class="
            mt-1
            font-title
            text-[0.72rem]
            font-bold
            uppercase
            tracking-[0.35em]
            text-primary
          "
        >
          VIAL
        </span>
      </div>
    </a>

    <!-- DESKTOP NAV -->
    <div
      class="
        hidden
        items-center
        gap-8
        lg:flex
      "
    >
      {#each navigationLinks as link}
        <a
          href={link.href}
          class="
            relative
            text-[13px]
            font-medium
            text-white/75
            transition-all
            duration-300
            hover:text-white
          "
        >
          {link.label}
        </a>
      {/each}
    </div>

    <!-- DESKTOP CTA -->
    <a
      href={`tel:+${businessInfo.phone.replace(/\s/g, '')}`}
      class="
        hidden
        items-center
        gap-2
        rounded-xl
        bg-primary
        px-4
        py-2.5
        text-sm
        font-semibold
        text-white
        transition-all
        duration-300
        hover:bg-primary-hover
        hover:shadow-primary
        lg:flex
      "
    >
      <Phone size={16} />

      <span>{businessInfo.phone}</span>
    </a>

    <!-- MOBILE BUTTON -->
    <button
      onclick={toggleMenu}
      class="
        flex
        h-10
        w-10
        items-center
        justify-center
        rounded-xl
        border
        border-white/5
        bg-white/5
        text-white
        transition-all
        duration-300
        hover:bg-white/10
        lg:hidden
      "
      aria-label="Toggle Menu"
    >
      {#if isMenuOpen}
        <X size={20} />
      {:else}
        <Menu size={20} />
      {/if}
    </button>
  </nav>

  <!-- MOBILE MENU -->
  {#if isMenuOpen}
    <div
      class="
        container-base
        mt-3
        overflow-hidden
        rounded-2xl
        border
        border-white/5
        bg-black/95
        backdrop-blur-2xl
        lg:hidden
      "
    >
      <div
        class="
          flex
          flex-col
          gap-2
          p-4
        "
      >
        {#each navigationLinks as link}
          <a
            href={link.href}
            onclick={closeMenu}
            class="
              rounded-xl
              px-4
              py-3
              text-sm
              font-medium
              text-white/75
              transition-all
              duration-300
              hover:bg-white/5
              hover:text-white
            "
          >
            {link.label}
          </a>
        {/each}

        <!-- MOBILE CTA -->
        <a
          href={`tel:+${businessInfo.phone.replace(/\s/g, '')}`}
          class="
            mt-2
            flex
            items-center
            justify-center
            gap-2
            rounded-xl
            bg-primary
            px-5
            py-3
            text-sm
            font-semibold
            text-white
            transition-all
            duration-300
            hover:bg-primary-hover
          "
        >
          <Phone size={18} />

          <span>{businessInfo.phone}</span>
        </a>
      </div>
    </div>
  {/if}
</header>
