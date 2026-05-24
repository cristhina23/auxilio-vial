<script>
  import { onMount } from 'svelte';

  import { Menu, X, Phone } from '@lucide/svelte';

  import {
    businessInfo,
    navigationLinks,
  } from '../../data/site.js';

  let isMenuOpen = $state(false);

  let activeSection = $state('inicio');

  const toggleMenu = () => {
    isMenuOpen = !isMenuOpen;
  };

  const closeMenu = () => {
    isMenuOpen = false;
  };

  onMount(() => {
    const sections = document.querySelectorAll('section[id]');

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            activeSection = entry.target.id;
          }
        });
      },
      {
        threshold: 0.6,
      }
    );

    sections.forEach((section) => {
      observer.observe(section);
    });

    return () => {
      sections.forEach((section) => {
        observer.unobserve(section);
      });
    };
  });
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
      <div class="flex">
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
          class={`
            relative
            pb-1
            text-[13px]
            font-medium
            transition-all
            duration-300

            ${
              activeSection === link.href.replace('#', '')
                ? 'text-white'
                : 'text-white/60 hover:text-white'
            }
          `}
        >
          {link.label}

          <span
            class={`
              absolute
              -bottom-[4px]
              left-0
              h-[2px]
              rounded-full
              bg-primary
              transition-all
              duration-300

              ${
                activeSection === link.href.replace('#', '')
                  ? 'w-full opacity-100'
                  : 'w-0 opacity-0'
              }
            `}
          />
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
        px-5
        py-3
        pr-6
        text-sm
        font-semibold
        text-white
        shadow-[0_0_25px_rgba(229,9,20,0.25)]
        transition-all
        duration-300
        hover:bg-primary-hover
        hover:scale-[1.02]
        hover:shadow-[0_0_35px_rgba(229,9,20,0.35)]
        lg:flex
      "
    >
      <Phone
        size={17}
        strokeWidth={2.5}
      />

      <span class="leading-none">
        {businessInfo.phone}
      </span>
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
            class={`
              rounded-xl
              px-4
              py-3
              text-sm
              font-medium
              transition-all
              duration-300

              ${
                activeSection === link.href.replace('#', '')
                  ? 'bg-primary text-white'
                  : 'text-white/75 hover:bg-white/5 hover:text-white'
              }
            `}
          >
            {link.label}
          </a>
        {/each}

        <!-- MOBILE CTA -->
         <button
          onclick={closeMenu}
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