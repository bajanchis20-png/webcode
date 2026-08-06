<script lang="ts">
    let nombre = $state('');
    let negocio = $state('');
    let tipoWeb = $state('Landing Page');
    let descripcion = $state('');
    let dominioBusqueda = $state('');

    function enviarWhatsApp(e: Event) {
        e.preventDefault();

        const telefono = '584149430559';
        const mensaje = `Hola, quiero solicitar mi página web con los siguientes datos:
- Nombre: ${nombre}
- Negocio/Empresa: ${negocio}
- Tipo de Web: ${tipoWeb}
- Qué deseo / Detalles: ${descripcion}`;

        const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
        window.open(url, '_blank');
    }

    function buscarDominioWhatsApp(e: Event) {
        e.preventDefault();
        if (!dominioBusqueda.trim()) return;

        const telefono = '584149430559';
        const mensaje = `Hola, me interesa consultar la disponibilidad del dominio "${dominioBusqueda}" para mi sitio web.`;

        const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
        window.open(url, '_blank');
    }
    // Puedes importar componentes adicionales aquí si lo deseas
</script>

<section class="bg-white text-slate-900 pt-16 sm:pt-24 md:pt-28 pb-32 sm:pb-36 md:pb-44 px-4 sm:px-6 lg:px-8 font-sans relative overflow-hidden border-b border-slate-200">
  
  <!-- Video de fondo responsive y optimizado -->
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <video 
      src="/slogan.mp4" 
      autoplay 
      loop 
      muted 
      playsinline 
      class="w-full h-full object-cover opacity-10 filter blur-[1px] scale-105"
    ></video>
    <div class="absolute inset-0 bg-gradient-to-b from-white/90 via-white/80 to-white"></div>
  </div>

  <div class="absolute top-12 left-1/2 -translate-x-1/2 w-[280px] sm:w-[500px] md:w-[650px] h-[160px] sm:h-[300px] md:h-[380px] bg-gradient-to-tr from-[#0071e3]/10 to-sky-400/10 blur-[100px] sm:blur-[140px] md:blur-[160px] pointer-events-none rounded-full z-1"></div>

  <!-- Contenedor Principal en Grid de 2 Columnas (Izquierda: Textos / Derecha: Tarjetas con video) -->
  <div class="max-w-[1200px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12 items-center relative z-10 w-full">
    
    <!-- COLUMNA IZQUIERDA: Títulos y CTAs -->
    <div class="lg:col-span-6 text-center lg:text-left flex flex-col items-center lg:items-start">
      
      <h1 class="text-3xl xs:text-4xl sm:text-5xl md:text-5xl font-extrabold tracking-tight text-slate-900 mb-5 leading-[1.15] uppercase">
        CREAMOS TU PÁGINA WEB <br class="hidden sm:inline" />
        <span class="bg-gradient-to-r from-[#0066cc] via-sky-600 to-indigo-600 bg-clip-text text-transparent inline-block mt-1">DISEÑADA PARA VENDER 24/7.</span>
      </h1>

      <p class="text-base sm:text-lg font-normal text-slate-600 max-w-xl mb-8 leading-relaxed">
        Arquitectura web minimalista de alta gama, velocidad de carga óptima y experiencia de usuario impecable. Impulsamos tu marca con máxima seguridad y transparencia operativa.
      </p>

      <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-3.5 w-full max-w-md mb-10">
        <a 
          href="#contacto" 
          class="w-full sm:w-auto bg-[#0071e3] hover:bg-[#0077ed] text-white font-medium text-base px-7 py-4 rounded-xl transition-all duration-300 text-center shadow-lg shadow-blue-500/25"
        >
          Solicitar Propuesta Gratis
        </a>
        <a 
          href="#paquetes" 
          class="w-full sm:w-auto bg-slate-100 hover:bg-slate-200 text-slate-800 font-medium text-base px-7 py-4 rounded-xl transition-all duration-300 border border-slate-300/80 text-center"
        >
          Ver Paquetes
        </a>
      </div>

      <!-- Métricas Compactas -->
      <div class="grid grid-cols-3 gap-3 w-full pt-6 border-t border-slate-200 text-center bg-[#f8fafc] backdrop-blur-md p-4 rounded-2xl border border-slate-200/80 shadow-sm">
        <div>
          <div class="text-xl sm:text-2xl font-bold text-slate-900">100%</div>
          <div class="text-[11px] text-slate-600 font-medium">Responsive</div>
        </div>
        <div class="border-x border-slate-200">
          <div class="text-xl sm:text-2xl font-bold text-slate-900">Incluido</div>
          <div class="text-[11px] text-slate-600 font-medium">Dominio & Hosting</div>
        </div>
        <div>
          <div class="text-xl sm:text-2xl font-bold text-slate-900">50/50</div>
          <div class="text-[11px] text-slate-600 font-medium">Pago Seguro</div>
        </div>
      </div>

    </div>

    <!-- COLUMNA DERECHA: Dos Tarjetas con Video (Hacemos tu web / Te enseñamos) -->
    <div class="lg:col-span-6 grid grid-cols-1 sm:grid-cols-2 gap-6 w-full">
      
      <!-- Tarjeta 1: Hacemos tu página web -->
      <div class="bg-[#f8fafc] rounded-3xl p-5 border border-slate-200 shadow-xl flex flex-col justify-between group hover:border-[#0071e3]/50 transition-all duration-300 text-left">
        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-900 mb-4 shadow-inner">
            <video 
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" 
              autoplay 
              muted 
              loop 
              playsinline
            >
              <source src="/slogan.mp4" type="video/mp4">
            </video>
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent"></div>
            <span class="absolute bottom-3 left-3 bg-[#0071e3] text-white text-[10px] font-bold uppercase tracking-wider px-2.5 py-1 rounded-md">Servicio Full</span>
          </div>

          <h3 class="text-lg font-bold text-slate-900 mb-2">Hacemos tu página web</h3>
          <p class="text-xs text-slate-600 leading-relaxed mb-4">
            Construimos tu sitio profesional desde cero, optimizado para vender 24/7 sin que te preocupes por nada técnico.
          </p>
        </div>

        <a 
          href="#contacto" 
          class="w-full bg-slate-900 hover:bg-[#0071e3] text-white text-xs font-semibold py-3 rounded-xl transition-colors text-center block"
        >
          Solicitar Servicio &gt;
        </a>
      </div>

      <!-- Tarjeta 2: Te enseñamos a hacer tu página web -->
      <div class="bg-[#f8fafc] rounded-3xl p-5 border border-slate-200 shadow-xl flex flex-col justify-between group hover:border-[#0071e3]/50 transition-all duration-300 text-left">
        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-900 mb-4 shadow-inner">
            <video 
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" 
              autoplay 
              muted 
              loop 
              playsinline
            >
              <source src="/agro.mp4" type="video/mp4">
            </video>
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent"></div>
            <span class="absolute bottom-3 left-3 bg-amber-500 text-slate-900 text-[10px] font-bold uppercase tracking-wider px-2.5 py-1 rounded-md">Academia IA</span>
          </div>

          <h3 class="text-lg font-bold text-slate-900 mb-2">Te enseñamos a crearla</h3>
          <p class="text-xs text-slate-600 leading-relaxed mb-4">
            Domina herramientas modernas y asistentes de IA con nuestro curso práctico para publicar tu propia web.
          </p>
        </div>

        <a 
          href="/educacion" 
          class="w-full bg-slate-900 hover:bg-[#0071e3] text-white text-xs font-semibold py-3 rounded-xl transition-colors text-center block"
        >
          Ver Programa &gt;
        </a>
      </div>

    </div>

  </div>

  <!-- Curva inferior decorativa -->
  <div class="absolute bottom-0 left-0 right-0 overflow-hidden leading-none z-20 pointer-events-none">
    <svg class="relative block w-full h-14 sm:h-20 text-[#f8fafc]" viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M0,0 C300,90 900,90 1200,0 L1200,120 L0,120 Z" fill="currentColor"></path>
    </svg>
  </div>
</section>

<!-- Sección de Buscador de Dominio adaptada a la paleta corporativa oscura (#0b0f19 y #0071e3) -->
<section class="py-20 px-4 bg-[#0b0f19] text-white font-sans text-center border-b border-slate-800">
  <div class="max-w-[850px] mx-auto">
    
    <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4 text-white">
      Obtén un dominio propio <br class="hidden sm:inline" /> para tu sitio web
    </h2>
    <p class="text-slate-400 text-sm sm:text-base max-w-xl mx-auto mb-10 font-normal">
      Verifica la disponibilidad de tu marca en internet al instante.
    </p>
    
    <!-- Formulario de búsqueda con estilo integrado a la web -->
    <form onsubmit={buscarDominioWhatsApp} class="mt-4 mb-4 max-w-[720px] mx-auto bg-[#121826] p-2 rounded-2xl sm:rounded-full flex flex-col sm:flex-row items-center shadow-2xl border border-white/10 gap-2 sm:gap-0">
      <input 
        type="text" 
        bind:value={dominioBusqueda}
        placeholder="Ingresa tu dominio ideal (ej. miempresa.com)" 
        required
        class="w-full sm:w-auto flex-grow bg-transparent px-6 py-4 text-white placeholder-slate-500 text-base focus:outline-none"
      />
      <button 
        type="submit"
        class="w-full sm:w-auto bg-[#0071e3] hover:bg-[#0077ed] text-white font-semibold text-base px-8 py-4 rounded-xl sm:rounded-full transition-all flex items-center justify-center gap-2 cursor-pointer shadow-lg"
      >
        <span>Buscar</span>
        <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M14 5l7 7m0 0l-7 7m7-7H3"/></svg>
      </button>
    </form>

    <p class="text-xs sm:text-sm text-slate-400 font-normal mt-4">
      Obtén un <span class="text-slate-200 underline underline-offset-2">dominio web</span> gratis durante un año con la compra de algun paquete con nosotros.
    </p>

  </div>
</section>

<section class="py-24 px-4 bg-white text-slate-900 font-sans border-t border-slate-200">
  <div class="max-w-[1100px] mx-auto text-center">
    
    <h2 class="text-3xl md:text-4xl font-bold mb-4 tracking-tight text-slate-900">
      Ingeniería de vanguardia en cada detalle.
    </h2>
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal">
      No solo creamos páginas bonitas; construimos activos digitales ultra rápidos, seguros y preparados para escalar.
    </p>

    <!-- Grid de características profesional y con un toque dinámico -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left">
      
      <!-- Tarjeta 1: Rendimiento -->
      <div class="group relative bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between transition-all duration-300 hover:-translate-y-1.5 hover:shadow-xl hover:shadow-slate-200/50 hover:border-[#0066cc]/40">
        <div class="absolute top-6 right-6 w-10 h-10 rounded-2xl bg-white border border-slate-200/80 flex items-center justify-center text-slate-400 group-hover:text-[#0066cc] group-hover:border-[#0066cc]/30 group-hover:rotate-12 transition-all duration-300 shadow-sm">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
        </div>
        <div class="pr-12">
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Rendimiento</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900 group-hover:text-[#0066cc] transition-colors duration-300">Velocidad extrema</h3>
          <p class="text-slate-600 text-sm leading-relaxed">Arquitectura optimizada para asegurar tiempos de carga casi instantáneos y retener a tus visitantes.</p>
        </div>
      </div>

      <!-- Tarjeta 2: Diseño UI/UX -->
      <div class="group relative bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between transition-all duration-300 hover:-translate-y-1.5 hover:shadow-xl hover:shadow-slate-200/50 hover:border-[#0066cc]/40">
        <div class="absolute top-6 right-6 w-10 h-10 rounded-2xl bg-white border border-slate-200/80 flex items-center justify-center text-slate-400 group-hover:text-[#0066cc] group-hover:border-[#0066cc]/30 group-hover:rotate-12 transition-all duration-300 shadow-sm">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
        </div>
        <div class="pr-12">
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Diseño UI/UX</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900 group-hover:text-[#0066cc] transition-colors duration-300">Estética impecable</h3>
          <p class="text-slate-600 text-sm leading-relaxed">Interfaces limpias y profesionales inspiradas en los más altos estándares visuales del mercado global.</p>
        </div>
      </div>

      <!-- Tarjeta 3: Escalabilidad -->
      <div class="group relative bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between transition-all duration-300 hover:-translate-y-1.5 hover:shadow-xl hover:shadow-slate-200/50 hover:border-[#0066cc]/40">
        <div class="absolute top-6 right-6 w-10 h-10 rounded-2xl bg-white border border-slate-200/80 flex items-center justify-center text-slate-400 group-hover:text-[#0066cc] group-hover:border-[#0066cc]/30 group-hover:rotate-12 transition-all duration-300 shadow-sm">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"/></svg>
        </div>
        <div class="pr-12">
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Escalabilidad</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900 group-hover:text-[#0066cc] transition-colors duration-300">Preparados para crecer</h3>
          <p class="text-slate-600 text-sm leading-relaxed">Bases sólidas que evolucionan fluidamente al mismo ritmo que el crecimiento de tu marca o negocio.</p>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- Sección de Autoridad: Proyectos Reales (Casos de Éxito) -->
<section id="proyectos" class="py-24 px-4 bg-[#f8fafc] text-slate-900 font-sans border-b border-slate-200">
  <div class="max-w-[1200px] mx-auto text-center">
    
    <div class="inline-block px-3 py-1 bg-blue-50 text-[#0066cc] text-xs font-semibold uppercase tracking-wider rounded-full mb-3">
      Resultados Reales y Comprobables
    </div>
    
    <h2 class="text-3xl md:text-5xl font-bold mt-2 mb-4 tracking-tight text-slate-900">
      Nuestros primeros proyectos
    </h2>
    
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal">
      Conoce sitios web oficiales que ya están operando con éxito en internet, generando confianza y clientes reales.
    </p>

    <!-- Grid de Proyectos -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-left items-stretch">
      
      <!-- Proyecto 1: Agrovenz -->
      <div class="bg-white p-8 rounded-3xl flex flex-col justify-between shadow-sm border border-slate-200/80 hover:shadow-xl transition-all duration-300 group">
        <div>
          <!-- Contenedor del Video -->
          <div class="relative w-full aspect-video mb-6 rounded-2xl overflow-hidden bg-slate-100 border border-slate-200 shadow-inner">
            <video 
              class="w-full h-full object-cover" 
              autoplay 
              muted 
              loop 
              playsinline
            >
              <source src="/agro.mp4" type="video/mp4">
              Tu navegador no soporta la reproducción de videos.
            </video>
          </div>

          <div class="flex items-center justify-between mb-4">
            <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider bg-blue-50 px-3 py-1 rounded-md">Plataforma Agroindustrial</span>
            <span class="text-xs text-emerald-600 font-medium flex items-center gap-1">● Online Activo</span>
          </div>
          <h3 class="text-2xl font-bold mb-2 text-slate-900 group-hover:text-[#0071e3] transition-colors">agrovenz.com</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Diseño corporativo estructurado para transmitir absoluta solidez, optimizado para una navegación clara, veloz y directa al grano.
          </p>
        </div>
        <div>
          <div class="flex items-center justify-between pt-4 border-t border-slate-100">
            <span class="text-xs text-slate-500 font-medium">Arquitectura a medida</span>
            <a 
              href="https://agrovenz.com" 
              target="_blank" 
              rel="noopener noreferrer" 
              class="text-sm font-semibold text-[#0071e3] hover:text-blue-700 flex items-center gap-1 group-hover:translate-x-1 transition-transform"
            >
              Visitar sitio &gt;
            </a>
          </div>
        </div>
      </div>

      <!-- Proyecto 2: Ebgamingshop -->
      <div class="bg-white p-8 rounded-3xl flex flex-col justify-between shadow-sm border border-slate-200/80 hover:shadow-xl transition-all duration-300 group">
        <div>
          <!-- Contenedor del Video -->
          <div class="relative w-full aspect-video mb-6 rounded-2xl overflow-hidden bg-slate-100 border border-slate-200 shadow-inner">
            <video 
              class="w-full h-full object-cover" 
              autoplay 
              muted 
              loop 
              playsinline
            >
              <source src="gaming.mp4" type="video/mp4">
              Tu navegador no soporta la reproducción de videos.
            </video>
          </div>

          <div class="flex items-center justify-between mb-4">
            <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider bg-blue-50 px-3 py-1 rounded-md">E-commerce / Tienda Online</span>
            <span class="text-xs text-emerald-600 font-medium flex items-center gap-1">● Online Activo</span>
          </div>
          <h3 class="text-2xl font-bold mb-2 text-slate-900 group-hover:text-[#0071e3] transition-colors">ebgamingshop.com</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Tienda virtual interactiva enfocada en maximizar conversiones, con catálogos dinámicos y un flujo de compra sumamente fluido.
          </p>
        </div>
        <div>
          <div class="flex items-center justify-between pt-4 border-t border-slate-100">
            <span class="text-xs text-slate-500 font-medium">Tienda Online Completa</span>
            <a 
              href="https://ebgamingshop.com" 
              target="_blank" 
              rel="noopener noreferrer" 
              class="text-sm font-semibold text-[#0071e3] hover:text-blue-700 flex items-center gap-1 group-hover:translate-x-1 transition-transform"
            >
              Visitar sitio &gt;
            </a>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- Sección de Paquetes y Precios (Clara, Transparente y Profesional) -->
<section id="paquetes" class="py-24 px-4 bg-white text-slate-900 font-sans">
  <div class="max-w-[1200px] mx-auto text-center">
    
    <div class="inline-block px-3 py-1 bg-slate-100 text-slate-700 text-xs font-semibold uppercase tracking-wider rounded-full mb-3">
      Inversión Inteligente
    </div>

    <h2 class="text-3xl md:text-5xl font-bold mb-4 tracking-tight text-slate-900">
      Nuestros Paquetes
    </h2>
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal">
      Soluciones adaptadas a cada etapa de tu negocio, con tarifas totalmente transparentes y esquemas de pago flexibles (50% al iniciar y 50% al entregar).
    </p>

    <!-- Grid de Paquetes -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left items-stretch">
      
      <!-- Paquete 1: Landing Page -->
      <div class="bg-[#f8fafc] p-8 rounded-3xl flex flex-col justify-between border border-slate-200 hover:border-slate-300 transition-all">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Ideal para empezar</span>
          <h3 class="text-2xl font-bold mt-2 mb-1 text-slate-900">Landing Page</h3>
          <p class="text-xs text-slate-500 mb-4">Emprendedores y profesionales independientes</p>
          <div class="text-3xl font-extrabold text-slate-900 mb-2">$150 – $180 <span class="text-sm font-normal text-slate-500">USD</span></div>
          <p class="text-xs text-emerald-600 font-semibold mb-6 flex items-center gap-1">⏱ Entrega estimada: 3 a 5 días</p>
          
          <ul class="space-y-3 text-sm text-slate-600 mb-8 border-t border-slate-200/60 pt-6">
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Estructura One-page fluida</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Hero Section, Beneficios y CTA</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Botón de WhatsApp directo</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Diseño 100% Responsivo y UI/UX</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Optimización SEO básica</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Dominio incluído por 1 año</li>
          </ul>
        </div>
        <a href="https://wa.me/584149430559?text=Hola,%20quiero%20elegir%20el%20paquete%20Landing%20Page." target="_blank" rel="noopener noreferrer" class="block text-center bg-slate-900 hover:bg-[#0071e3] text-white text-sm font-semibold py-3 rounded-full transition-colors">
          Elegir Landing
        </a>
      </div>

      <!-- Paquete 2: Página Web Profesional (Destacado) -->
      <div class="bg-slate-900 text-white p-8 rounded-3xl flex flex-col justify-between relative border-2 border-[#0071e3] transform md:-translate-y-2">
        <div class="absolute -top-3.5 left-1/2 transform -translate-x-1/2 bg-[#0071e3] text-white text-[11px] uppercase font-bold px-4 py-1 rounded-full tracking-wider">
          Más popular / PyMEs
        </div>
        <div>
          <span class="text-xs font-semibold text-blue-400 uppercase tracking-wider">Empresas en Crecimiento</span>
          <h3 class="text-2xl font-bold mt-2 mb-1 text-white">Web Profesional</h3>
          <p class="text-xs text-slate-400 mb-4">Negocios que buscan presencia corporativa completa</p>
          <div class="text-3xl font-extrabold text-white mb-2">$200 – $250 <span class="text-sm font-normal text-slate-400">USD</span></div>
          <p class="text-xs text-blue-400 font-semibold mb-6 flex items-center gap-1">⏱ Entrega estimada: 3 a 5 días</p>
          
          <ul class="space-y-3 text-sm text-slate-300 mb-8 border-t border-slate-800 pt-6">
            <li class="flex items-start"><span class="text-blue-400 font-bold mr-2">✓</span> 4 a 6 páginas internas</li>
            <li class="flex items-start"><span class="text-blue-400 font-bold mr-2">✓</span> Diseño 100% Responsivo de lujo</li>
            <li class="flex items-start"><span class="text-blue-400 font-bold mr-2">✓</span> Blog integrado y SEO avanzado</li>
            <li class="flex items-start"><span class="text-blue-400 font-bold mr-2">✓</span> Formularios de contacto seguros</li>
            <li class="flex items-start"><span class="text-blue-400 font-bold mr-2">✓</span> Dominio incluído por 1 año</li>
          </ul>
        </div>
        <a href="https://wa.me/584149430559?text=Hola,%20quiero%20elegir%20el%20paquete%20Web%20Profesional." target="_blank" rel="noopener noreferrer" class="block text-center bg-[#0071e3] hover:bg-blue-600 text-white text-sm font-semibold py-3 rounded-full transition-colors">
          Elegir Profesional
        </a>
      </div>

      <!-- Paquete 3: Tienda Online -->
      <div class="bg-[#f8fafc] p-8 rounded-3xl flex flex-col justify-between border border-slate-200 hover:border-slate-300 transition-all">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">E-commerce</span>
          <h3 class="text-2xl font-bold mt-2 mb-1 text-slate-900">Tienda Online</h3>
          <p class="text-xs text-slate-500 mb-4">Venta masiva de productos físicos o digitales</p>
          <div class="text-3xl font-extrabold text-slate-900 mb-2">$200 – $350+ <span class="text-sm font-normal text-slate-500">USD</span></div>
          <p class="text-xs text-emerald-600 font-semibold mb-6 flex items-center gap-1">⏱ Entrega estimada: 3 a 5 días</p>
          
          <ul class="space-y-3 text-sm text-slate-600 mb-8 border-t border-slate-200/60 pt-6">
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Catálogo completo y variantes</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Pasarelas de pago configuradas</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Carrito y Checkout optimizado</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Gestión de catálogo y stock</li>
            <li class="flex items-start"><span class="text-[#0071e3] font-bold mr-2">✓</span> Dominio incluído por 1 año</li>
          </ul>
        </div>
        <a href="https://wa.me/584149430559?text=Hola,%20quiero%20elegir%20el%20paquete%20Tienda%20Online." target="_blank" rel="noopener noreferrer" class="block text-center bg-slate-900 hover:bg-[#0071e3] text-white text-sm font-semibold py-3 rounded-full transition-colors">
          Elegir Tienda
        </a>
      </div>

    </div>
  </div>
</section>

<!-- Sección de Proceso de Trabajo (Garantía de Cero Riesgos) -->
<section class="py-24 px-4 bg-[#f8fafc] text-slate-900 font-sans border-t border-slate-200">
  <div class="max-w-[1200px] mx-auto text-center">
    
    <div class="inline-block px-3 py-1 bg-blue-50 text-[#0066cc] text-xs font-semibold uppercase tracking-wider rounded-full mb-3">
      Proceso Seguro
    </div>

    <h2 class="text-3xl md:text-5xl font-bold mb-4 tracking-tight text-slate-900">
      ¿Cómo trabajamos contigo?
    </h2>
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal">
      Queremos que te sientas 100% seguro. Por eso nuestro flujo es transparente, sin sorpresas y con resultados visuales antes de pagar cualquier anticipo.
    </p>

    <!-- Grid de Pasos -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-left items-stretch max-w-[900px] mx-auto">
      
      <!-- Paso 1 -->
      <div class="bg-white p-8 rounded-3xl flex flex-col justify-between shadow-sm border border-slate-200">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Paso 01</span>
          <h3 class="text-2xl font-bold mt-2 mb-2 text-slate-900">Propuesta Inicial</h3>
          <p class="text-sm text-slate-600 leading-relaxed">
            Analizamos tu marca, requerimientos y objetivos. Te entregamos una propuesta inicial con la estructura y diseño visual orientado a resultados, ¡totalmente gratis!
          </p>
        </div>
        <div class="mt-8 pt-4 border-t border-slate-100 flex items-center justify-between">
          <span class="text-xs font-semibold text-emerald-600 bg-emerald-50 px-3 py-1 rounded-full">
            100% Gratis y sin compromiso
          </span>
        </div>
      </div>

      <!-- Paso 2 -->
      <div class="bg-white p-8 rounded-3xl flex flex-col justify-between shadow-sm border border-slate-200">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Paso 02</span>
          <h3 class="text-2xl font-bold mt-2 mb-2 text-slate-900">Abono y Desarrollo</h3>
          <p class="text-sm text-slate-600 leading-relaxed">
            Si la propuesta te encanta, realizas el abono del 50% inicial para dar inicio formal al desarrollo completo, optimización e instalación en tu servidor.
          </p>
        </div>
        <div class="mt-8 pt-4 border-t border-slate-100">
          <a href="https://wa.me/584149430559?text=Hola,%20quiero%20solicitar%20mi%20propuesta%20inicial%20gratuita." target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-1 text-sm font-semibold text-[#0066cc] hover:text-blue-700">
            Solicitar propuesta ahora &gt;
          </a>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- Sección de Beneficios / Ingeniería de Vanguardia -->


<section id="contacto" class="py-24 px-4 bg-[#0b0f19] text-white font-sans relative overflow-hidden">
  
  <!-- Efectos de luz ambiental sutiles -->
  <div class="absolute bottom-0 right-1/2 translate-x-1/2 w-[500px] h-[300px] bg-gradient-to-tr from-[#0071e3]/15 to-[#38bdf8]/15 blur-[120px] pointer-events-none rounded-full"></div>

  <div class="max-w-[700px] mx-auto relative z-10">
    
    <div class="text-center mb-12">
    
      <h2 class="text-3xl md:text-5xl font-bold tracking-tight mb-4 text-white">
        Diseña tu web ideal
      </h2>
      <p class="text-slate-400 text-base md:text-lg max-w-xl mx-auto font-normal">
        Cuéntanos sobre tu proyecto rellenando este formulario. Al enviarlo, te conectaremos directamente por WhatsApp con los detalles listos.
      </p>
    </div>

    <!-- Formulario -->
    <form onsubmit={enviarWhatsApp} class="bg-[#121826] p-8 md:p-10 rounded-3xl border border-white/10 shadow-2xl space-y-6">
      
      <!-- Nombre -->
      <div>
        <label for="nombre" class="block text-sm font-medium text-slate-300 mb-2">Tu Nombre</label>
        <input 
          type="text" 
          id="nombre" 
          bind:value={nombre} 
          required 
          placeholder="Ej. Carlos Pérez" 
          class="w-full bg-[#0b0f19] border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-slate-600 focus:outline-none focus:border-[#0071e3] transition-colors text-sm"
        />
      </div>

      <!-- Negocio o Marca -->
      <div>
        <label for="negocio" class="block text-sm font-medium text-slate-300 mb-2">Nombre de tu Negocio o Empresa</label>
        <input 
          type="text" 
          id="negocio" 
          bind:value={negocio} 
          required 
          placeholder="Ej. Inversiones Globales C.A." 
          class="w-full bg-[#0b0f19] border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-slate-600 focus:outline-none focus:border-[#0071e3] transition-colors text-sm"
        />
      </div>

      <!-- Tipo de Página Web -->
      <div>
        <label for="tipoWeb" class="block text-sm font-medium text-slate-300 mb-2">¿Qué tipo de web deseas?</label>
        <select 
          id="tipoWeb" 
          bind:value={tipoWeb} 
          class="w-full bg-[#0b0f19] border border-white/10 rounded-xl px-4 py-3.5 text-white focus:outline-none focus:border-[#0071e3] transition-colors text-sm cursor-pointer"
        >
          <option value="Landing Page ($150 - $180)">Landing Page ($150 - $180)</option>
          <option value="Web Profesional ($200 - $250)">Web Profesional ($200 - $250)</option>
          <option value="Tienda Online / E-commerce ($200 - $350+)">Tienda Online / E-commerce ($200 - $350+)</option>
          <option value="Proyecto Personalizado / Otro">Proyecto Personalizado / Otro</option>
        </select>
      </div>

      <!-- Descripción / Qué desea -->
      <div>
        <label for="descripcion" class="block text-sm font-medium text-slate-300 mb-2">¿Sobre qué es tu negocio y qué funciones necesitas?</label>
        <textarea 
          id="descripcion" 
          bind:value={descripcion} 
          required 
          rows="4" 
          placeholder="Ej. Vendemos repuestos industriales y necesitamos un catálogo ordenado con botón directo a WhatsApp..."
          class="w-full bg-[#0b0f19] border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-slate-600 focus:outline-none focus:border-[#0071e3] transition-colors text-sm resize-none"
        ></textarea>
      </div>

      <!-- Botón Enviar a WhatsApp -->
      <button 
        type="submit" 
        class="w-full bg-[#0071e3] hover:bg-[#0077ed] text-white font-semibold text-base py-4 rounded-xl transition-all shadow-lg active:scale-[0.99] flex items-center justify-center gap-2 cursor-pointer"
      >
        <span>Enviar Solicitud por WhatsApp</span>
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
      </button>

      <p class="text-xs text-center text-slate-500 pt-1">
        Al hacer clic, se abrirá WhatsApp automáticamente con tu mensaje estructurado.
      </p>

    </form>

  </div>
</section>

<!-- Sección de Cierre / Llamado a la Acción final -->
<section class="py-20 px-4 bg-[#0b0f19] text-white text-center font-sans">
  <div class="max-w-[800px] mx-auto">
    <h2 class="text-3xl md:text-5xl font-bold tracking-tight mb-4">
      ¿Listo para despegar en internet?
    </h2>
    <p class="text-slate-400 text-lg mb-8">
      Escríbenos hoy y recibe tu propuesta inicial completamente gratis. Sin compromisos.
    </p>
    <a 
      href="https://wa.me/584149430559?text=Hola,%20quiero%20comenzar%20a%20desarrollar%20mi%20página%20web." 
      target="_blank"
      rel="noopener noreferrer"
      class="inline-block bg-[#0071e3] hover:bg-[#0077ed] text-white font-semibold text-base px-8 py-4 rounded-full transition-all hover:scale-105"
    >
      Contáctanos por WhatsApp Ahora
    </a>
  </div>
</section>