<script lang="ts">
let nombre = $state('');
    let negocio = $state('');
    let tipoWeb = $state('Landing Page');
    let descripcion = $state('');

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
    // Puedes importar componentes adicionales aquí si lo deseas
</script>

<section class="bg-[#0b0f19] text-white pt-16 sm:pt-20 md:pt-24 pb-28 sm:pb-32 md:pb-40 px-4 sm:px-6 lg:px-8 text-center font-sans relative overflow-hidden">
  
  <!-- Video como fondo responsive de toda la sección -->
  <div class="absolute inset-0 z-0 overflow-hidden">
    <video 
      src="/slogan.mp4" 
      autoplay 
      loop 
      muted 
      playsinline 
      class="w-full h-full object-cover opacity-60 filter blur-[1px] scale-105"
    ></video>
    <!-- Capa oscura sutil para mantener el contraste adaptable -->
    <div class="absolute inset-0 bg-[#0b0f19]/70"></div>
  </div>

  <!-- Efectos de luz ambiental optimizados y adaptados a pantallas móviles -->
  <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[280px] sm:w-[450px] md:w-[600px] h-[180px] sm:h-[280px] md:h-[350px] bg-gradient-to-tr from-[#0071e3]/15 to-[#38bdf8]/15 blur-[90px] sm:blur-[120px] md:blur-[140px] pointer-events-none rounded-full z-1"></div>

  <div class="max-w-[1100px] mx-auto flex flex-col items-center relative z-10 w-full">
    
    <!-- Título Principal con escala fluida y responsive extrema -->
    <h1 class="text-2xl xs:text-3xl sm:text-4xl md:text-5xl lg:text-7xl font-extrabold tracking-tight text-white mb-4 sm:mb-6 leading-[1.2] sm:leading-[1.18] md:leading-[1.15] max-w-5xl px-1 sm:px-0">
      Tu negocio merece una presencia digital <br class="hidden sm:inline" />
      <span class="bg-gradient-to-r from-blue-400 via-sky-300 to-indigo-300 bg-clip-text text-transparent">diseñada para vender 24/7.</span>
    </h1>

    <!-- Subtítulo descriptivo con tamaño adaptable -->
    <p class="text-sm sm:text-base md:text-xl font-normal text-slate-300 max-w-2xl mb-8 sm:mb-10 leading-relaxed drop-shadow-md px-2 sm:px-0">
      Arquitectura web minimalista de alta gama, velocidad de carga óptima y experiencia de usuario impecable. Impulsamos tu marca con máxima seguridad y transparencia operativa.
    </p>

    <!-- CTAs Principales con diseño 100% responsive y adaptados a touch targets -->
    <div class="flex flex-col sm:flex-row items-center justify-center gap-3 sm:gap-4 w-full max-w-md mb-10 sm:mb-16 px-2 sm:px-0">
      <a 
        href="#contacto" 
        class="w-full sm:w-auto bg-[#0071e3] hover:bg-[#0077ed] text-white font-semibold text-sm sm:text-base px-6 sm:px-8 py-3.5 sm:py-4 rounded-xl transition-all duration-300 hover:scale-[1.02] active:scale-[0.98] text-center shadow-lg shadow-blue-500/10"
      >
        Solicitar Propuesta Gratis
      </a>
      <a 
        href="#paquetes" 
        class="w-full sm:w-auto bg-white/5 hover:bg-white/10 text-slate-200 hover:text-white font-medium text-sm sm:text-base px-6 sm:px-7 py-3.5 sm:py-4 rounded-xl transition-all duration-300 border border-white/15 backdrop-blur-sm text-center"
      >
        Ver Paquetes y Tarifas
      </a>
    </div>

    <!-- Barra de Métricas y Respaldo Institucional adaptable -->
    <div class="grid grid-cols-2 md:grid-cols-3 gap-3 sm:gap-6 md:gap-8 max-w-3xl w-full pt-6 sm:pt-8 md:pt-10 border-t border-white/15 text-center bg-[#0b0f19]/40 backdrop-blur-sm p-3.5 sm:p-5 md:p-6 rounded-2xl shadow-inner mx-auto">
      <div class="space-y-1">
        <div class="text-lg sm:text-2xl md:text-3xl font-bold tracking-tight text-white drop-shadow-sm">100%</div>
        <div class="text-[11px] sm:text-xs md:text-sm text-slate-300 font-medium">Responsive & Mobile-First</div>
      </div>
      <div class="space-y-1">
        <div class="text-lg sm:text-2xl md:text-3xl font-bold tracking-tight text-white drop-shadow-sm">Incluido</div>
        <div class="text-[11px] sm:text-xs md:text-sm text-slate-300 font-medium">Dominio y Hosting (1 Año)</div>
      </div>
      <div class="col-span-2 md:col-span-1 space-y-1">
        <div class="text-lg sm:text-2xl md:text-3xl font-bold tracking-tight text-white drop-shadow-sm">50% / 50%</div>
        <div class="text-[11px] sm:text-xs md:text-sm text-slate-300 font-medium">Esquema de Pago Seguro</div>
      </div>
    </div>

  </div>

  <!-- Curva inferior decorativa de color blanco -->
  <div class="absolute bottom-0 left-0 right-0 overflow-hidden leading-none z-20 pointer-events-none">
    <svg class="relative block w-full h-12 sm:h-20 md:h-28 text-white" viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M0,0 C300,90 900,90 1200,0 L1200,120 L0,120 Z" fill="currentColor"></path>
    </svg>
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

    <!-- Grid de características minimalista -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left">
      <div class="bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Rendimiento</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900">Velocidad extrema</h3>
          <p class="text-slate-600 text-sm leading-relaxed">Arquitectura optimizada para asegurar tiempos de carga casi instantáneos y retener a tus visitantes.</p>
        </div>
      </div>

      <div class="bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Diseño UI/UX</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900">Estética impecable</h3>
          <p class="text-slate-600 text-sm leading-relaxed">Interfaces limpias y profesionales inspiradas en los más altos estándares visuales del mercado global.</p>
        </div>
      </div>

      <div class="bg-[#f8fafc] p-8 rounded-3xl border border-slate-200/60 flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Escalabilidad</span>
          <h3 class="text-xl font-bold mt-2 mb-3 text-slate-900">Preparados para crecer</h3>
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