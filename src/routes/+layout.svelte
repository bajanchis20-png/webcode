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
    .animate-fade-in-down:nth-child(5) { animation-delay: 0.20s; }
    
    .animate-btn-in {
        animation: fade-in-down 0.35s cubic-bezier(0.16, 1, 0.3, 1) 0.24s forwards;
        opacity: 0;
    }
</style>

<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>

<!-- Header Flotante Estilo Apple Adaptado a Diseño Claro -->
<header class="sticky top-3 z-50 px-4 font-sans transition-all">
  <nav class="max-w-[980px] mx-auto bg-white/80 backdrop-blur-md border border-slate-200/80 text-slate-900 rounded-full px-6 h-12 flex items-center justify-between text-[12px] font-normal tracking-[-0.01em] shadow-lg shadow-slate-200/50 relative z-50">
    
    <!-- Logo o Título de la empresa -->
   <a href="/" class="flex items-center opacity-90 hover:opacity-100 transition-opacity py-1 whitespace-nowrap">
    <img src="/logo2.png" alt="Nombre de tu empresa" class="h-8 w-auto">
</a>
    
    <!-- Navegación de Escritorio -->
    <div class="hidden md:flex items-center space-x-7 text-slate-600 font-medium">
      <a href="/" class="hover:text-slate-900 transition-colors">Inicio</a>
      <a href="#paquetes" class="hover:text-slate-900 transition-colors">Servicios</a>
      <a href="#proyectos" class="hover:text-slate-900 transition-colors">Proyectos</a>
      <a href="#contacto" class="hover:text-slate-900 transition-colors">Contacto</a>
      <a href="/educacion" class="hover:text-slate-900 transition-colors">Educación</a>
    </div>

    <!-- Acciones de Escritorio -->
    <div class="hidden md:flex items-center space-x-4">
      <a 
        href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." 
        target="_blank" 
        rel="noopener noreferrer" 
        class="bg-[#0071e3] hover:bg-[#0077ed] text-white px-3.5 py-1.5 rounded-full text-[11px] font-semibold transition-all hover:scale-[1.02] active:scale-95 shadow-md shadow-blue-500/20"
      >
        Comenzar
      </a>
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-600 hover:text-slate-900 transition-colors p-1">
        <Icon icon="lucide:shopping-bag" width="16" height="16" />
      </a>
    </div>

    <!-- Controles Móviles (Arreglado para visibilidad total) -->
    <div class="flex items-center space-x-2 md:hidden">
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-700 hover:text-slate-900 transition-colors p-1.5">
        <Icon icon="lucide:shopping-bag" width="18" height="18" />
      </a>

      <!-- Botón de Hamburguesa / X con contraste y visibilidad garantizados -->
      <button 
        onclick={toggleMenu} 
        class="flex items-center justify-center w-9 h-9 rounded-full bg-slate-100 border border-slate-200 text-slate-900 focus:outline-none relative z-50 cursor-pointer shadow-sm" 
        aria-label={menuOpen ? 'Cerrar menú' : 'Abrir menú'}
      >
        <div class="relative w-4 h-3.5 flex flex-col justify-between">
          <span class="absolute block h-[2px] w-full bg-slate-900 rounded-full transition-all duration-300 origin-center {menuOpen ? 'top-[6px] rotate-45' : 'top-0'}"></span>
          <span class="absolute block h-[2px] w-full bg-slate-900 rounded-full transition-all duration-300 top-[6px] {menuOpen ? 'opacity-0 scale-x-0' : 'opacity-100'}"></span>
          <span class="absolute block h-[2px] w-full bg-slate-900 rounded-full transition-all duration-300 origin-center {menuOpen ? 'top-[6px] -rotate-45' : 'top-[12px]'}"></span>
        </div>
      </button>
    </div>
  </nav>

  <!-- Menú Desplegable Móvil en sintonía con el diseño claro -->
  {#if menuOpen}
    <div class="fixed inset-0 w-full h-screen bg-white/95 backdrop-blur-xl z-40 px-6 pt-24 pb-8 font-sans md:hidden flex flex-col justify-start overflow-y-auto border-b border-slate-200">
      <div class="flex flex-col space-y-4 pt-4">
        <a href="/" onclick={toggleMenu} class="block text-xl font-semibold text-slate-900 py-2 border-b border-slate-200 animate-fade-in-down">Inicio</a>
        <a href="#paquetes" onclick={toggleMenu} class="block text-xl font-semibold text-slate-600 py-2 border-b border-slate-200 animate-fade-in-down">Servicios</a>
        <a href="#proyectos" onclick={toggleMenu} class="block text-xl font-semibold text-slate-600 py-2 border-b border-slate-200 animate-fade-in-down">Proyectos</a>
        <a href="#contacto" onclick={toggleMenu} class="block text-xl font-semibold text-slate-600 py-2 border-b border-slate-200 animate-fade-in-down">Contacto</a>
        <a href="/educacion" onclick={toggleMenu} class="block text-xl font-semibold text-slate-600 py-2 border-b border-slate-200 animate-fade-in-down">Educación</a>
      </div>

      <div class="animate-btn-in mt-6">
        <a 
          href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." 
          target="_blank"
          rel="noopener noreferrer"
          onclick={toggleMenu} 
          class="w-full block text-center bg-[#0071e3] hover:bg-[#0077ed] text-white py-3.5 rounded-xl font-medium text-sm transition-all shadow-lg shadow-blue-500/20"
        >
          Comenzar Ahora
        </a>
      </div>
    </div>
  {/if}
</header>

<main class="min-h-screen bg-white text-slate-900 font-normal font-sans selection:bg-[#0071e3] selection:text-white">
    {@render children()}
</main>

<!-- Footer Corporativo de Alto Nivel adaptado a tema claro -->
<footer class="bg-slate-50 text-slate-600 text-[12px] font-normal leading-relaxed border-t border-slate-200 font-sans">
  <div class="max-w-[1120px] mx-auto px-6 py-16">
    <div class="grid grid-cols-1 md:grid-cols-12 gap-12 pb-14 border-b border-slate-200">
      
      <!-- Columna de Marca -->
      <div class="md:col-span-5 space-y-4">
        <h3 class="text-xl font-bold text-slate-900 opacity-90 tracking-tight">EBWebCode&Design</h3>
        <p class="text-slate-600 text-[13px] leading-relaxed max-w-sm">
          Soluciones de ingeniería y desarrollo web de alta gama. Optimizamos la presencia digital de empresas exigentes bajo rigurosos estándares de rendimiento, estética y conversión.
        </p>
      </div>

      <!-- Enlaces de Navegación -->
      <div class="md:col-span-7 grid grid-cols-2 sm:grid-cols-3 gap-8">
        <div>
          <h4 class="text-slate-900 font-semibold mb-4 text-[13px]">Servicios</h4>
          <ul class="space-y-2.5">
            <li><a href="#paquetes" class="hover:text-slate-900 transition-colors">Desarrollo Web</a></li>
            <li><a href="#paquetes" class="hover:text-slate-900 transition-colors">E-commerce</a></li>
            <li><a href="#paquetes" class="hover:text-slate-900 transition-colors">Arquitectura UI/UX</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-slate-900 font-semibold mb-4 text-[13px]">Compañía</h4>
          <ul class="space-y-2.5">
            <li><a href="#proyectos" class="hover:text-slate-900 transition-colors">Casos de Éxito</a></li>
            <li><a href="#contacto" class="hover:text-slate-900 transition-colors">Soporte Directo</a></li>
            <li><a href="/educacion" class="hover:text-slate-900 transition-colors">Educación</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-slate-900 font-semibold mb-4 text-[13px]">Legal</h4>
          <ul class="space-y-2.5">
            <li><a href="/" class="hover:text-slate-900 transition-colors">Privacidad</a></li>
            <li><a href="/" class="hover:text-slate-900 transition-colors">Términos de Servicio</a></li>
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