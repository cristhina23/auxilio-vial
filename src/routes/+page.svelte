<script>
    import Navbar from '$lib/components/Navbar.svelte';
    import Hero from '$lib/components/Hero.svelte';
    import Benefits from '$lib/components/Benefits.svelte';
    import Services from '$lib/components/Services.svelte';
    import WhyUs from '$lib/components/WhyUs.svelte';
    import HowItWorks from '$lib/components/HowItWorks.svelte';
    import Testimonials from '$lib/components/Testimonials.svelte';
    import Footer from '$lib/components/Footer.svelte';
    import WhatsAppButton from '$lib/components/WhatsAppButton.svelte';
    import { onMount } from 'svelte';
    onMount(() => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.2 });
        document.querySelectorAll('.section').forEach(el => observer.observe(el));
    });
</script>





<Navbar class="section"/>
<Hero class="section"/>
<Benefits class="section"/>
<Services class="section"/>
<WhyUs class="section"/>
<HowItWorks class="section"/>
<Testimonials class="section"/>
<Footer class="section"/>
<WhatsAppButton class="section"/>
<style>
  :global(.section) {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s ease-out, transform 0.6s ease-out;
  }
  :global(.section.visible) {
    opacity: 1;
    transform: none;
  }
</style>
