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

<!-- Header Flotante Estilo Apple Adaptado al Tema Oscuro/Moderno -->
<header class="sticky top-3 z-50 px-4 font-sans transition-all">
  <nav class="max-w-[980px] mx-auto bg-[#0b0f19]/80 backdrop-blur-md border border-white/10 text-white rounded-full px-6 h-12 flex items-center justify-between text-[12px] font-normal tracking-[-0.01em] shadow-lg shadow-black/40 relative z-50">
    
    <!-- Título en lugar del logo -->
   <a href="/" class="flex items-center opacity-90 hover:opacity-100 transition-opacity py-1 whitespace-nowrap">
    <img src="/logo4.png" alt="Nombre de tu empresa" class="h-8 w-auto">
</a>
    
    <!-- Navegación de Escritorio -->
    <div class="hidden md:flex items-center space-x-8 text-slate-300 font-medium">
      <a href="/" class="hover:text-white transition-colors">Inicio</a>
      <a href="#paquetes" class="hover:text-white transition-colors">Servicios</a>
      <a href="#proyectos" class="hover:text-white transition-colors">Proyectos</a>
      <a href="#contacto" class="hover:text-white transition-colors">Contacto</a>
    </div>

    <!-- Acciones de Escritorio -->
    <div class="hidden md:flex items-center space-x-5">
      <a 
        href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." 
        target="_blank" 
        rel="noopener noreferrer" 
        class="bg-[#0071e3] hover:bg-[#0077ed] text-white px-3.5 py-1.5 rounded-full text-[11px] font-semibold transition-all hover:scale-[1.02] active:scale-95 shadow-md shadow-blue-500/20"
      >
        Comenzar
      </a>
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-300 hover:text-white transition-colors p-1">
        <Icon icon="lucide:shopping-bag" width="16" height="16" />
      </a>
    </div>

    <!-- Controles Móviles -->
    <div class="flex items-center space-x-3 md:hidden">
      <a href="#paquetes" aria-label="Planes y Paquetes" class="text-slate-300 hover:text-white transition-colors p-1">
        <Icon icon="lucide:shopping-bag" width="16" height="16" />
      </a>

      <!-- Botón de Hamburguesa / X con z-index superior garantizado -->
      <button 
        onclick={toggleMenu} 
        class="flex items-center justify-center w-8 h-8 focus:outline-none relative z-50 cursor-pointer" 
        aria-label={menuOpen ? 'Cerrar menú' : 'Abrir menú'}
      >
        <div class="relative w-4 h-3.5 flex flex-col justify-between">
          <span class="absolute block h-[2px] w-full bg-white rounded-full transition-all duration-300 origin-center {menuOpen ? 'top-[6px] rotate-45' : 'top-0'}"></span>
          <span class="absolute block h-[2px] w-full bg-white rounded-full transition-all duration-300 top-[6px] {menuOpen ? 'opacity-0 scale-x-0' : 'opacity-100'}"></span>
          <span class="absolute block h-[2px] w-full bg-white rounded-full transition-all duration-300 origin-center {menuOpen ? 'top-[6px] -rotate-45' : 'top-[12px]'}"></span>
        </div>
      </button>
    </div>
  </nav>

  <!-- Menú Desplegable Móvil en sintonía con el diseño oscuro de alta gama -->
  {#if menuOpen}
    <div class="fixed inset-0 w-full h-screen bg-[#0b0f19]/95 backdrop-blur-xl z-40 px-6 pt-24 pb-8 font-sans md:hidden flex flex-col justify-start overflow-y-auto border-b border-white/10">
      <div class="flex flex-col space-y-4 pt-4">
        <a href="/" onclick={toggleMenu} class="block text-xl font-semibold text-white py-2 border-b border-white/10 animate-fade-in-down">Inicio</a>
        <a href="#paquetes" onclick={toggleMenu} class="block text-xl font-semibold text-slate-300 py-2 border-b border-white/10 animate-fade-in-down">Servicios</a>
        <a href="#proyectos" onclick={toggleMenu} class="block text-xl font-semibold text-slate-300 py-2 border-b border-white/10 animate-fade-in-down">Proyectos</a>
        <a href="#contacto" onclick={toggleMenu} class="block text-xl font-semibold text-slate-300 py-2 border-b border-white/10 animate-fade-in-down">Contacto</a>
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

<main class="min-h-screen bg-[#0b0f19] text-white font-normal font-sans selection:bg-[#0071e3] selection:text-white">
    {@render children()}
</main>

<!-- Footer Corporativo de Alto Nivel -->
<footer class="bg-[#07090f] text-slate-400 text-[12px] font-normal leading-relaxed border-t border-white/[0.06] font-sans">
  <div class="max-w-[1120px] mx-auto px-6 py-16">
    <div class="grid grid-cols-1 md:grid-cols-12 gap-12 pb-14 border-b border-white/[0.06]">
      
      <!-- Columna de Marca -->
      <div class="md:col-span-5 space-y-4">
        <!-- Título en lugar del logo en el footer -->
        <h3 class="text-xl font-bold text-white opacity-90 tracking-tight">EBWebCode&Design</h3>
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

<!-- Botón Flotante Global de WhatsApp -->
<a 
  href="https://wa.me/584149430559?text=Hola,%20vengo%20de%20su%20sitio%20web%20y%20deseo%20más%20información." 
  target="_blank" 
  rel="noopener noreferrer"
  class="fixed bottom-6 right-6 z-50 bg-[#25D366] hover:bg-[#20ba5a] text-white p-3.5 rounded-full shadow-2xl transition-all duration-300 hover:scale-110 flex items-center justify-center group"
  aria-label="Contactar por WhatsApp"
>
  <svg class="w-6 h-6 fill-current" viewBox="0 0 24 24">
    <path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372s-1.04 1.016-1.04 2.479 1.065 2.876 1.213 3.074c.149.198 2.095 3.2 5.076 4.487.709.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/>
  </svg>
</a>