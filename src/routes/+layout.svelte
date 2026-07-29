<script lang="ts">
    import './layout.css';
    import favicon from '$lib/assets/favicon.svg';
    import Icon from '@iconify/svelte';

    let { children } = $props();
    let menuOpen = $state(false);

    function toggleMenu() {
        menuOpen = !menuOpen;
        if (typeof document !== 'undefined') {
            document.body.style.overflow = menuOpen ? 'hidden' : '';
        }
    }
</script>

<style>
    @keyframes fade-in-down {
        0% { opacity: 0; transform: translateY(-10px); }
        100% { opacity: 1; transform: translateY(0); }
    }
    .animate-fade-in-down {
        animation: fade-in-down 0.4s ease-out forwards;
        opacity: 0;
    }
    .animate-fade-in-down:nth-child(1) { animation-delay: 0.05s; }
    .animate-fade-in-down:nth-child(2) { animation-delay: 0.10s; }
    .animate-fade-in-down:nth-child(3) { animation-delay: 0.15s; }
    .animate-fade-in-down:nth-child(4) { animation-delay: 0.20s; }
    
    .animate-btn-in {
        animation: fade-in-down 0.4s ease-out 0.25s forwards;
        opacity: 0;
    }
</style>

<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>

<header class="sticky top-0 z-50 bg-[rgba(255,255,255,0.8)] backdrop-blur-md border-b border-[#d2d2d7] text-[#1d1d1f] font-sans transition-all">
  <nav class="max-w-[1024px] mx-auto px-4 h-11 flex items-center justify-between text-[12px] font-normal tracking-[-0.01em]">
    
    <a href="/" class="flex items-center opacity-90 hover:opacity-100 transition-opacity py-1">
      <img src="/logo.png" alt="Logo" class="h-[21px] w-auto object-contain" />
    </a>
    
    <div class="hidden md:flex items-center space-x-9 text-[#1d1d1f]">
      <a href="/" class="hover:text-[#0066cc] transition-colors">Inicio</a>
      <a href="#servicios" class="hover:text-[#0066cc] transition-colors">Servicios</a>
      <a href="#proyectos" class="hover:text-[#0066cc] transition-colors">Proyectos</a>
      <a href="#contacto" class="hover:text-[#0066cc] transition-colors">Contacto</a>
    </div>

    <div class="hidden md:flex items-center space-x-6">
      <a href="#contacto" class="bg-[#0071e3] hover:bg-[#0077ed] text-white px-3 py-1 rounded-full text-[11px] font-medium transition-all">
        Comenzar
      </a>
      <a href="#carrito" aria-label="Bolsa de compra" class="text-[#1d1d1f] hover:text-[#0066cc] transition-colors">
        <Icon icon="lucide:shopping-bag" width="16" height="16" />
      </a>
    </div>

    <div class="flex items-center space-x-4 md:hidden">
      <a href="#carrito" aria-label="Bolsa de compra" class="text-[#1d1d1f] hover:text-[#0066cc] transition-colors">
        <Icon icon="lucide:shopping-bag" width="16" height="16" />
      </a>

      <button 
        onclick={toggleMenu} 
        class="flex items-center justify-center w-6 h-6 -mr-1 focus:outline-none z-50 group" 
        aria-label={menuOpen ? 'Cerrar menú' : 'Abrir menú'}
      >
        <div class="relative w-4 h-3 transition-transform duration-300 {menuOpen ? 'rotate-[135deg]' : ''}">
          <span 
            class="absolute block h-[1.5px] w-full bg-[#1d1d1f] rounded-full transform transition-all duration-300 ease-in-out top-0 {menuOpen ? 'rotate-90 top-[5px]' : ''}"
          ></span>
          <span 
            class="absolute block h-[1.5px] w-full bg-[#1d1d1f] rounded-full transform transition-all duration-300 ease-in-out top-[5px] {menuOpen ? 'top-[5px] opacity-0' : ''}"
          ></span>
          <span 
            class="absolute block h-[1.5px] w-full bg-[#1d1d1f] rounded-full transform transition-all duration-300 ease-in-out top-[10px] {menuOpen ? 'top-[5px]' : ''}"
          ></span>
        </div>
      </button>
    </div>
  </nav>

  <!-- Menú Desplegable Móvil con el botón más cerca de los enlaces -->
  {#if menuOpen}
    <div class="fixed left-0 top-[44px] w-full h-[calc(100vh-44px)] bg-white z-40 px-6 py-8 font-sans md:hidden flex flex-col overflow-y-auto border-t border-[#d2d2d7]">
      <div class="flex flex-col space-y-4 mb-8">
        <a href="/" onclick={toggleMenu} class="block text-4xl font-semibold text-[#1d1d1f] py-2 animate-fade-in-down">Inicio</a>
        <a href="#servicios" onclick={toggleMenu} class="block text-4xl font-semibold text-[#1d1d1f] py-2 animate-fade-in-down">Servicios</a>
        <a href="#proyectos" onclick={toggleMenu} class="block text-4xl font-semibold text-[#1d1d1f] py-2 animate-fade-in-down">Proyectos</a>
        <a href="#contacto" onclick={toggleMenu} class="block text-4xl font-semibold text-[#1d1d1f] py-2 animate-fade-in-down">Contacto</a>
      </div>

      <div class="animate-btn-in">
        <a 
          href="#contacto" 
          onclick={toggleMenu} 
          class="w-full block text-center bg-[#0071e3] text-white py-4 rounded-2xl font-medium text-lg shadow-lg transform transition-all duration-500 ease-out"
        >
          Comenzar
        </a>
      </div>
    </div>
  {/if}
</header>

<main class="min-h-screen bg-white text-[#1d1d1f] font-normal font-sans">
    {@render children()}
</main>

<footer class="bg-[#f5f5f7] text-[#86868b] text-[11px] font-normal leading-relaxed border-t border-[#d2d2d7] font-sans">
  <div class="max-w-[1024px] mx-auto px-4 py-8">
    <div class="border-b border-[#d2d2d7] pb-6 mb-6">
      <p class="text-[#86868b] text-[11px] leading-normal">
        Diseñamos y desarrollamos páginas web profesionales con altos estándares de rendimiento y diseño para impulsar tu negocio al siguiente nivel. Cada proyecto se adapta de forma única a los estándares visuales más exigentes del mercado actual.
      </p>
    </div>
    
    <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-8">
      <div>
        <h4 class="text-[#1d1d1f] font-semibold mb-3 text-[12px]">Servicios</h4>
        <ul class="space-y-2">
          <li><a href="#servicios" class="hover:text-[#1d1d1f] transition-colors">Desarrollo Web</a></li>
          <li><a href="#servicios" class="hover:text-[#1d1d1f] transition-colors">E-commerce</a></li>
          <li><a href="#servicios" class="hover:text-[#1d1d1f] transition-colors">Optimización UI/UX</a></li>
        </ul>
      </div>
      <div>
        <h4 class="text-[#1d1d1f] font-semibold mb-3 text-[12px]">Empresa</h4>
        <ul class="space-y-2">
          <li><a href="#proyectos" class="hover:text-[#1d1d1f] transition-colors">Casos de Éxito</a></li>
          <li><a href="#contacto" class="hover:text-[#1d1d1f] transition-colors">Contacto</a></li>
        </ul>
      </div>
      <div>
        <h4 class="text-[#1d1d1f] font-semibold mb-3 text-[12px]">Recursos</h4>
        <ul class="space-y-2">
          <li><a href="/" class="hover:text-[#1d1d1f] transition-colors">Soporte Técnico</a></li>
          <li><a href="/" class="hover:text-[#1d1d1f] transition-colors">Documentación</a></li>
        </ul>
      </div>
      <div>
        <h4 class="text-[#1d1d1f] font-semibold mb-3 text-[12px]">Legal</h4>
        <ul class="space-y-2">
          <li><a href="/" class="hover:text-[#1d1d1f] transition-colors">Privacidad</a></li>
          <li><a href="/" class="hover:text-[#1d1d1f] transition-colors">Términos de uso</a></li>
        </ul>
      </div>
    </div>

    <div class="flex flex-col md:flex-row justify-between items-center pt-6 border-t border-[#d2d2d7] text-[#86868b]">
      <p>Copyright © 2026. Todos los derechos reservados.</p>
      <p class="mt-2 md:mt-0">Desarrollo web profesional.</p>
    </div>
  </div>
</footer>