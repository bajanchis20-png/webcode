<script lang="ts">
    // Puedes importar componentes adicionales aquí si lo deseas
</script>

<!-- Sección Hero Principal Estilo Apple -->
<section class="bg-[#f5f5f7] text-[#1d1d1f] pt-16 pb-20 px-4 text-center font-sans overflow-hidden">
  <div class="max-w-[1024px] mx-auto flex flex-col items-center">
    
    <!-- Logo + Texto Principal -->
    <div class="flex flex-wrap items-center justify-center gap-3 mb-3">
      <img src="/logo.png" alt="Logo" class="h-10 md:h-14 w-auto object-contain inline-block align-middle" />
      <h1 class="text-3xl md:text-5xl lg:text-6xl font-semibold tracking-tight text-[#1d1d1f] uppercase inline-block align-middle">
        Hacemos tu página web
      </h1>
    </div>

    <!-- Subtítulo descriptivo -->
    <p class="text-lg md:text-2xl font-normal text-[#86868b] max-w-xl mb-6 tracking-tight">
      Diseño impecable. Alto rendimiento. Listo para escalar tu negocio.
    </p>

    <!-- Botón de acción estilo Apple -->
    <div class="mb-14">
      <a 
        href="#contacto" 
        class="inline-block bg-[#0071e3] hover:bg-[#0077ed] text-white font-medium text-sm md:text-base px-5 py-2 rounded-full transition-all shadow-sm"
      >
        Comenzar
      </a>
    </div>

    <!-- Mockup / Imagen Central Destacada -->
    <div class="w-full max-w-[750px] px-4 transform hover:scale-[1.01] transition-transform duration-700">
      <img 
        src="/home.png" 
        alt="Vista previa del desarrollo web profesional" 
        class="w-full h-auto object-contain mx-auto drop-shadow-[0_20px_50px_rgba(0,0,0,0.12)] rounded-2xl"
      />
    </div>

  </div>
</section>

<!-- Sección Estilo Promoción Apple (Diseño Responsive) -->
<section class="bg-[#f5f5f7] text-[#1d1d1f] pt-20 px-4 text-center font-sans overflow-hidden border-t border-[#d2d2d7]">
  <div class="max-w-[1024px] mx-auto flex flex-col items-center">
    
    <!-- Título Principal unificado -->
    <h2 class="text-3xl md:text-5xl lg:text-6xl font-semibold tracking-tight text-[#1d1d1f] mb-3">
      Diseño Responsive
    </h2>

    <!-- Subtítulo descriptivo unificado -->
    <p class="text-lg md:text-2xl font-normal text-[#86868b] max-w-xl mb-6 tracking-tight">
      Garantice una presencia digital impecable con funcionalidad óptima y adaptación automática a cualquier pantalla.
    </p>

    <!-- Botón de acción estilo Apple -->
    <div class="mb-12">
      <a 
        href="#contacto" 
        class="inline-block bg-[#0071e3] hover:bg-[#0077ed] text-white font-medium text-sm md:text-base px-5 py-2 rounded-full transition-all shadow-sm"
      >
        Contratar
      </a>
    </div>

    <!-- Imagen Responsive más grande y pegada al fondo -->
    <div class="w-full max-w-[950px] px-0 transform hover:scale-[1.01] transition-transform duration-700">
      <img 
        src="/responsive.png" 
        alt="Desarrollo web profesional y personalizado" 
        class="w-full h-auto object-contain mx-auto drop-shadow-[0_20px_40px_rgba(0,0,0,0.08)] block"
      />
    </div>

  </div>
</section>

<!-- Nueva Sección Estilo Grid Doble (Estilo Promoción de Productos Apple) -->
<section class="py-12 px-4 bg-[#f5f5f7] text-[#1d1d1f] font-sans border-t border-[#d2d2d7]">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 md:grid-cols-2 gap-4">
    
    <!-- Bloque 1: Carrito de compras + buscador -->
    <div class="bg-[#fbfbfd] rounded-3xl p-8 md:p-12 text-center flex flex-col items-center justify-between overflow-hidden shadow-sm">
      <div>
        <h2 class="text-3xl md:text-4xl font-semibold tracking-tight mb-2 text-[#1d1d1f]">
          Carrito de compras + buscador
        </h2>
        <p class="text-base md:text-lg text-[#86868b] mb-6 font-normal">
          Optimiza la experiencia de tus clientes con herramientas de búsqueda avanzada y gestión de compras fluida.
        </p>
        <div class="flex items-center justify-center space-x-4 mb-8">
          <a href="#contacto" class="bg-[#0071e3] hover:bg-[#0077ed] text-white text-sm font-medium px-4 py-1.5 rounded-full transition-all">
            Más información
          </a>
        
        </div>
      </div>
      <div class="w-full max-w-[500px] mt-4 transform hover:scale-[1.02] transition-transform duration-500">
        <img src="/carrito.png" alt="Carrito de compras y buscador" class="w-full h-auto object-contain mx-auto" />
      </div>
    </div>

    <!-- Bloque 2: Dominio y hosting por 1 año -->
    <div class="bg-[#fbfbfd] rounded-3xl p-8 md:p-12 text-center flex flex-col items-center justify-between overflow-hidden shadow-sm">
      <div>
        <h2 class="text-3xl md:text-4xl font-semibold tracking-tight mb-2 text-[#1d1d1f]">
          Dominio y hosting por 1 año
        </h2>
        <p class="text-base md:text-lg text-[#86868b] mb-6 font-normal">
          Todo lo necesario para poner tu sitio en marcha de forma segura, rápida y sin costos sorpresa iniciales.
        </p>
        <div class="flex items-center justify-center space-x-4 mb-8">
          <a href="#contacto" class="bg-[#0071e3] hover:bg-[#0077ed] text-white text-sm font-medium px-4 py-1.5 rounded-full transition-all">
            Más información
          </a>
          <a href="#contacto" class="text-[#0066cc] hover:underline text-sm font-medium flex items-center">
            Comprar &gt;
          </a>
        </div>
      </div>
      <div class="w-full max-w-[500px] mt-4 transform hover:scale-[1.02] transition-transform duration-500">
        <img src="/hosting.png" alt="Dominio y hosting por 1 año" class="w-full h-auto object-contain mx-auto" />
      </div>
    </div>

  </div>
</section>

<!-- Sección Secundaria de Características o Servicios -->
<section class="py-20 px-4 bg-white text-[#1d1d1f] font-sans border-t border-[#d2d2d7]">
  <div class="max-w-[1024px] mx-auto text-center">
    <h2 class="text-3xl md:text-4xl font-semibold mb-4 tracking-tight">
      Ingeniería de vanguardia en cada detalle.
    </h2>
    <p class="text-[#86868b] text-base md:text-lg max-w-2xl mx-auto mb-12 font-normal">
      Optimizados al máximo para garantizar velocidad, accesibilidad y una experiencia visual inigualable en cualquier pantalla.
    </p>

    <!-- Grid de características minimalista -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left">
      <div class="bg-[#f5f5f7] p-8 rounded-3xl flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Rendimiento</span>
          <h3 class="text-xl font-semibold mt-2 mb-3 text-[#1d1d1f]">Velocidad extrema</h3>
          <p class="text-[#86868b] text-sm leading-relaxed">Desarrollados con tecnología moderna para asegurar tiempos de carga casi instantáneos.</p>
        </div>
      </div>

      <div class="bg-[#f5f5f7] p-8 rounded-3xl flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Diseño UI/UX</span>
          <h3 class="text-xl font-semibold mt-2 mb-3 text-[#1d1d1f]">Estética impecable</h3>
          <p class="text-[#86868b] text-sm leading-relaxed">Interfaces limpias y elegantes inspiradas en los más altos estándares visuales de la industria.</p>
        </div>
      </div>

      <div class="bg-[#f5f5f7] p-8 rounded-3xl flex flex-col justify-between">
        <div>
          <span class="text-xs font-semibold text-[#0066cc] uppercase tracking-wider">Escalabilidad</span>
          <h3 class="text-xl font-semibold mt-2 mb-3 text-[#1d1d1f]">Preparados para crecer</h3>
          <p class="text-[#86868b] text-sm leading-relaxed">Arquitectura sólida y adaptable que evoluciona al mismo ritmo que las necesidades de tu marca.</p>
        </div>
      </div>
    </div>
  </div>
</section>
