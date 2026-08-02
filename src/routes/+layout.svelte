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
        0% { opacity: 0; transform: translateY(-8px); }
        100% { opacity: 1; transform: translateY(0); }
    }
    .animate-fade-in-down {
        animation: fade-in-down 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        opacity: 0;
    }
    .animate-fade-in-down:nth-child(1) { animation-delay: 0.04s; }
    .animate-fade-in-down:nth-child(2) { animation-delay: 0.08s; }
    .animate-fade-in-down:nth-child(3) { animation-delay: 0.12s; }
    .animate-fade-in-down:nth-child(4) { animation-delay: 0.16s; }
    
    .animate-btn-in {
        animation: fade-in-down 0.35s cubic-bezier(0.16, 1, 0.3, 1) 0.2s forwards;
        opacity: 0;
    }
</style>

<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>

<!-- Header Corporativo Estilizado -->
<header class="sticky top-0 z-50 bg-[#0b0f19]/85 backdrop-blur-md border-b border-white/[0.06] text-white font-sans transition-all">
  <nav class="max-w-[1120px] mx-auto px-6 h-16 flex items-center justify-between text-[13px] font-normal tracking-[-0.01em]">
    
    <!-- Logo Institucional -->
    <a href="/" class="flex items-center opacity-95 hover:opacity-100 transition-opacity py-1">
      <img src="/logo.png" alt="Logo Corporativo" class="h-7 w-auto object-contain brightness-200" />
    </a>
    
    <!-- Navegación de Escritorio -->
    <div class="hidden md:flex items-center space-x-9 text-slate-300 font-medium">
      <a href="/" class="hover:text-white transition-colors">Inicio</a>
      <a href="#paquetes" class="hover:text-white transition-colors">Servicios</a>
      <a href="#proyectos" class="hover:text-white transition-colors">Proyectos</a>
      <a href="#contacto" class="hover:text-white transition-colors">Contacto</a>
    </div>

    <!-- Acciones de Escritorio -->
    <div class="hidden md:flex items-center space-x-6">
      <a 
        href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." 
        target="_blank" 
        rel="noopener noreferrer" 
        class="bg-[#0071e3] hover:bg-[#0077ed] text-white px-4 py-2 rounded-full text-[12px] font-semibold transition-all active:scale-95"
      >
        Comenzar
      </a>
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-300 hover:text-white transition-colors p-1">
        <Icon icon="lucide:shopping-bag" width="18" height="18" />
      </a>
    </div>

    <!-- Controles Móviles -->
    <div class="flex items-center space-x-4 md:hidden">
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-300 hover:text-white transition-colors p-1">
        <Icon icon="lucide:shopping-bag" width="18" height="18" />
      </a>

      <button 
        onclick={toggleMenu} 
        class="flex items-center justify-center w-8 h-8 focus:outline-none z-50" 
        aria-label={menuOpen ? 'Cerrar menú' : 'Abrir menú'}
      >
        <div class="relative w-5 h-4 transition-transform duration-300 {menuOpen ? 'rotate-[135deg]' : ''}">
          <span class="absolute block h-[1.5px] w-full bg-white rounded-full transition-all duration-300 top-0 {menuOpen ? 'rotate-90 top-[7px]' : ''}"></span>
          <span class="absolute block h-[1.5px] w-full bg-white rounded-full transition-all duration-300 top-[7px] {menuOpen ? 'opacity-0' : ''}"></span>
          <span class="absolute block h-[1.5px] w-full bg-white rounded-full transition-all duration-300 top-[14px] {menuOpen ? 'top-[7px]' : ''}"></span>
        </div>
      </button>
    </div>
  </nav>

  <!-- Menú Desplegable Móvil -->
  {#if menuOpen}
    <div class="fixed left-0 top-16 w-full h-[calc(100vh-4rem)] bg-[#0b0f19] z-40 px-8 py-10 font-sans md:hidden flex flex-col justify-between border-t border-white/[0.06]">
      <div class="flex flex-col space-y-6 pt-2">
        <a href="/" onclick={toggleMenu} class="block text-2xl font-medium text-white py-1 animate-fade-in-down">Inicio</a>
        <a href="#paquetes" onclick={toggleMenu} class="block text-2xl font-medium text-slate-300 py-1 animate-fade-in-down">Servicios</a>
        <a href="#proyectos" onclick={toggleMenu} class="block text-2xl font-medium text-slate-300 py-1 animate-fade-in-down">Proyectos</a>
        <a href="#contacto" onclick={toggleMenu} class="block text-2xl font-medium text-slate-300 py-1 animate-fade-in-down">Contacto</a>
      </div>

      <div class="animate-btn-in pb-6">
        <a 
          href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." 
          target="_blank"
          rel="noopener noreferrer"
          onclick={toggleMenu} 
          class="w-full block text-center bg-[#0071e3] hover:bg-[#0077ed] text-white py-3.5 rounded-xl font-medium text-base transition-all"
        >
          Comenzar Ahora
        </a>
      </div>
    </div>
  {/if}
</header>

<main class="min-h-screen bg-[#0b0f19] text-white font-normal font-sans selection:bg-[#0071e3] selection:text-white">
    {@render children()}
</main>

<!-- Footer Corporativo de Alto Nivel -->
<footer class="bg-[#07090f] text-slate-400 text-[12px] font-normal leading-relaxed border-t border-white/[0.06] font-sans">
  <div class="max-w-[1120px] mx-auto px-6 py-16">
    <div class="grid grid-cols-1 md:grid-cols-12 gap-12 pb-14 border-b border-white/[0.06]">
      
      <!-- Columna de Marca -->
      <div class="md:col-span-5 space-y-4">
        <img src="/logo.png" alt="Logo Corporativo" class="h-6 w-auto object-contain brightness-200 opacity-90" />
        <p class="text-slate-400 text-[13px] leading-relaxed max-w-sm">
          Soluciones de ingeniería y desarrollo web de alta gama. Optimizamos la presencia digital de empresas exigentes bajo rigurosos estándares de rendimiento, estética y conversión.
        </p>
      </div>

      <!-- Enlaces de Navegación -->
      <div class="md:col-span-7 grid grid-cols-2 sm:grid-cols-3 gap-8">
        <div>
          <h4 class="text-white font-semibold mb-4 text-[13px]">Servicios</h4>
          <ul class="space-y-2.5">
            <li><a href="#paquetes" class="hover:text-white transition-colors">Desarrollo Web</a></li>
            <li><a href="#paquetes" class="hover:text-white transition-colors">E-commerce</a></li>
            <li><a href="#paquetes" class="hover:text-white transition-colors">Arquitectura UI/UX</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-white font-semibold mb-4 text-[13px]">Compañía</h4>
          <ul class="space-y-2.5">
            <li><a href="#proyectos" class="hover:text-white transition-colors">Casos de Éxito</a></li>
            <li><a href="#contacto" class="hover:text-white transition-colors">Soporte Directo</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-white font-semibold mb-4 text-[13px]">Legal</h4>
          <ul class="space-y-2.5">
            <li><a href="/" class="hover:text-white transition-colors">Privacidad</a></li>
            <li><a href="/" class="hover:text-white transition-colors">Términos de Servicio</a></li>
          </ul>
        </div>
      </div>

    </div>

    <!-- Pie de página inferior -->
    <div class="flex flex-col sm:flex-row justify-between items-center pt-8 text-slate-500 text-[12px] gap-4">
      <p>© 2026. Todos los derechos reservados.</p>
      <p>Excelencia técnica y diseño orientado a resultados.</p>
    </div>
  </div>
</footer>