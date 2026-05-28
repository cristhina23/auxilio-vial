<script lang="ts">
  import { Phone } from '@lucide/svelte';
  const whatsappNumber = '+51987654321'; // TODO: replace with actual number
  const defaultMessage = encodeURIComponent('¡Hola! Necesito ayuda con...');
  const href = `https://wa.me/${whatsappNumber}?text=${defaultMessage}`;
</script>

<a href={href} target="_blank" rel="noopener" class="whatsapp-float">
  <Phone size={24} />
</a>

<style>
  .section {
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease-out;
  }

  .section.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .whatsapp-float {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    background: #25D366;
    color: white;
    border-radius: 50%;
    width: 56px;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    z-index: 1000;
    transition: transform 0.2s;
    animation: pulse 2.5s ease-in-out infinite, float 3s ease-in-out infinite alternate;
  }
  @keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.07); }
    100% { transform: scale(1); }
  }
  @keyframes float {
    from { transform: translateY(0); }
    to { transform: translateY(-8px); }
  }
  .whatsapp-float:hover { transform: scale(1.07); }
</style>
