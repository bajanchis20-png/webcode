<script lang="ts">
    // Estado para la gestión del carrito interactivo y carrito flotante
    let carrito = $state<{ titulo: string; precio: number; tipo: string }[]>([]);
    let mostrarNotificacion = $state(false);
    let mensajeNotificacion = $state('');
    let carritoAbierto = $state(false);

    function agregarAlCarrito(titulo: string, precio: number, tipo: string) {
        const existe = carrito.some(item => item.titulo === titulo);
        if (!existe) {
            carrito.push({ titulo, precio, tipo });
            mensajeNotificacion = `¡"${titulo}" agregado al carrito!`;
        } else {
            mensajeNotificacion = `"${titulo}" ya está en tu carrito.`;
        }

        mostrarNotificacion = true;
        setTimeout(() => {
            mostrarNotificacion = false;
        }, 3500);
    }

    function eliminarDelCarrito(index: number) {
        carrito.splice(index, 1);
    }

    function calcularTotal() {
        return carrito.reduce((acc, item) => acc + item.precio, 0);
    }

    function finalizarCompraWhatsApp() {
        if (carrito.length === 0) return;

        const telefono = '584149430559';
        let detalleCursos = carrito.map(item => `- ${item.titulo} ($${item.precio} USD)`).join('\n');
        let total = calcularTotal();

        const mensaje = `Hola, quiero finalizar la compra de los siguientes programas educativos:
${detalleCursos}
- Total a pagar: $${total} USD

Por favor, indíquenmen los pasos para procesar el pago.`;

        const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
        window.open(url, '_blank');
    }
</script>

<!-- Notificación flotante superior -->
{#if mostrarNotificacion}
    <div class="fixed top-20 right-6 z-50 bg-slate-900 text-white px-6 py-3 rounded-2xl shadow-2xl border border-white/20 flex items-center gap-3">
        <span class="text-emerald-400 font-bold">✓</span>
        <p class="text-sm font-medium">{mensajeNotificacion}</p>
    </div>
{/if}

<!-- Botón Flotante de Carrito -->
<button 
    onclick={() => carritoAbierto = !carritoAbierto}
    class="fixed bottom-6 right-6 z-50 bg-[#0071e3] hover:bg-[#0077ed] text-white p-4 rounded-full shadow-2xl transition-all duration-300 hover:scale-110 flex items-center justify-center gap-2 cursor-pointer group"
    aria-label="Abrir Carrito"
>
    <div class="relative flex items-center justify-center">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
        {#if carrito.length > 0}
            <span class="absolute -top-2 -right-2 bg-amber-500 text-slate-900 text-[10px] font-extrabold w-5 h-5 rounded-full flex items-center justify-center shadow-md">
                {carrito.length}
            </span>
        {/if}
    </div>
</button>

<!-- Panel Desplegable del Carrito Flotante -->
{#if carritoAbierto}
    <div class="fixed bottom-24 right-6 z-50 w-[350px] sm:w-[380px] bg-slate-900 text-white rounded-3xl p-6 border border-slate-700 shadow-2xl text-left">
        <div class="flex items-center justify-between pb-3 border-b border-slate-800 mb-4">
            <h3 class="text-base font-bold text-white flex items-center gap-2">
                <span>🛒 Tu Carrito</span>
                <span class="bg-blue-500/20 text-blue-400 text-xs px-2 py-0.5 rounded-full font-semibold">{carrito.length}</span>
            </h3>
            <button onclick={() => carritoAbierto = false} class="text-slate-400 hover:text-white text-sm font-semibold cursor-pointer">✕</button>
        </div>

        {#if carrito.length === 0}
            <p class="text-xs text-slate-400 text-center py-6">Tu carrito está vacío. Agrega un curso para comenzar.</p>
        {:else}
            <div class="space-y-3 mb-4 max-h-60 overflow-y-auto pr-1">
                {#each carrito as item, index}
                    <div class="flex items-center justify-between bg-slate-800 p-3 rounded-2xl border border-slate-700 text-xs">
                        <div>
                            <h4 class="font-bold text-white">{item.titulo}</h4>
                            <span class="text-slate-400">${item.precio} USD</span>
                        </div>
                        <button onclick={() => eliminarDelCarrito(index)} class="text-rose-400 hover:text-rose-300 font-semibold p-1 cursor-pointer">Eliminar</button>
                    </div>
                {/each}
            </div>

            <div class="pt-3 border-t border-slate-800 space-y-3">
                <div class="flex items-center justify-between text-sm">
                    <span class="text-slate-300 font-medium">Total:</span>
                    <span class="text-lg font-extrabold text-white">${calcularTotal()} USD</span>
                </div>

                <button 
                    type="button"
                    onclick={finalizarCompraWhatsApp}
                    class="w-full bg-[#25D366] hover:bg-[#20ba5a] text-white font-semibold text-xs py-3.5 rounded-xl transition-all shadow-md flex items-center justify-center gap-2 cursor-pointer"
                >
                    <span>Comprar por WhatsApp</span>
                    <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372s-1.04 1.016-1.04 2.479 1.065 2.876 1.213 3.074c.149.198 2.095 3.2 5.076 4.487.709.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/></svg>
                </button>
            </div>
        {/if}
    </div>
{/if}

<!-- HERO PRINCIPAL -->
<section class="bg-white text-slate-900 pt-24 sm:pt-32 md:pt-40 pb-28 sm:pb-36 px-4 sm:px-6 lg:px-8 text-center font-sans relative overflow-hidden border-b border-blue-500/20">
  <!-- Efectos de luz ambiental de alto rendimiento y conversión -->
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,rgba(0,113,227,0.1)_0%,transparent_65%)]"></div>
  </div>

  <div class="absolute top-12 left-1/2 -translate-x-1/2 w-[350px] sm:w-[700px] md:w-[950px] h-[200px] sm:h-[380px] bg-gradient-to-tr from-[#0071e3]/20 via-sky-400/20 to-indigo-600/10 blur-[130px] sm:blur-[180px] pointer-events-none rounded-full z-1"></div>

  <div class="max-w-[1150px] mx-auto flex flex-col items-center relative z-10 w-full">
    <h1 class="text-3xl xs:text-4xl sm:text-6xl md:text-7xl font-black tracking-tight text-slate-900 mb-6 leading-[1.06] max-w-5xl uppercase">
      Crea páginas web profesionales y <span class="bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 bg-clip-text text-transparent inline-block mt-1 drop-shadow-[0_0_35px_rgba(0,113,227,0.3)]">gana dinero real</span> haciéndolo.
    </h1>

    <!-- Subtítulo persuasivo -->
    <p class="text-base sm:text-xl md:text-2xl font-normal text-slate-600 max-w-3xl mb-12 leading-relaxed">
      Domina herramientas modernas, automatiza procesos con <strong class="text-slate-900 font-bold bg-[#0071e3]/10 px-2 py-0.5 rounded border border-[#0071e3]/25">Inteligencia Artificial</strong> y conviértete en un creador web altamente cotizado en el mercado global.
    </p>

    <!-- CTAs de conversión con el estilo de botón solicitado -->
    <div class="flex flex-col sm:flex-row gap-4 w-full sm:w-auto justify-center items-center">
    <a 
  href="#catalogo-cursos" 
  class="w-full sm:w-auto inline-flex items-center justify-center gap-3 bg-slate-100 hover:bg-slate-200 text-slate-800 font-medium text-base px-7 py-4 rounded-xl transition-all duration-300 border border-slate-300/80 text-center"
>
  <span>VER CURSOS Y EMPEZAR A GANAR</span>
  <svg class="w-5 h-5 transition-transform hover:translate-y-1 text-slate-700" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M19 14l-7 7m0 0l-7-7m7 7V3"/></svg>
</a>
    </div>

    <!-- Indicadores de confianza rápidos -->
    <div class="mt-16 flex flex-wrap justify-center items-center gap-6 sm:gap-12 text-slate-600 text-xs sm:text-sm font-medium border-t border-slate-200 pt-8 w-full max-w-4xl">
      <div class="flex items-center gap-2">
        <svg class="w-5 h-5 text-[#0071e3]" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
        <span>Acceso inmediato 24/7</span>
      </div>
      <div class="flex items-center gap-2">
        <svg class="w-5 h-5 text-[#0071e3]" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
        <span>Metodología 100% práctica</span>
      </div>
      <div class="flex items-center gap-2">
        <svg class="w-5 h-5 text-[#0071e3]" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
        <span>Enfoque en monetización rápida</span>
      </div>
    </div>

  </div>
</section>

<!-- SECCIÓN 1: ¿QUÉ APRENDERÁS? -->
<section class="bg-white text-slate-900 py-16 sm:py-20 md:py-24 px-4 sm:px-6 lg:px-8 border-b border-blue-500/25 relative overflow-hidden">
  <!-- Contenedor general adaptado para dispositivos móviles y pantallas grandes -->
  <div class="absolute inset-0 z-0 grid grid-cols-1 lg:grid-cols-2 overflow-hidden pointer-events-none">
    <div class="hidden lg:block bg-white"></div>
    <div class="relative w-full h-full overflow-hidden opacity-30 lg:opacity-100">
      <!-- Video de fondo con comportamiento responsive fluido -->
      <video autoplay muted loop playsinline class="absolute inset-0 w-full h-full object-cover">
        <source src="aprender.mp4" type="video/mp4">
        Tu navegador no soporta videos en HTML5.
      </video>
      <!-- Capas de fundido adaptadas para garantizar máxima legibilidad en móviles y desktop -->
      <div class="absolute inset-0 bg-gradient-to-t lg:bg-gradient-to-r from-white via-white/85 lg:via-white/70 to-white/95 lg:to-transparent backdrop-blur-[1px]"></div>
    </div>
  </div>

  <!-- Efectos de luz ambiental dinámicos y escalados para pantallas pequeñas -->
  <div class="absolute top-0 left-1/2 lg:left-1/4 -translate-x-1/2 lg:translate-x-0 w-[300px] sm:w-[450px] lg:w-[500px] h-[250px] sm:h-[300px] lg:h-[350px] bg-[#0071e3]/10 blur-[100px] sm:blur-[120px] lg:blur-[140px] pointer-events-none rounded-full z-10"></div>
  
  <div class="max-w-[1100px] mx-auto relative z-20">
    <div class="text-center max-w-3xl mx-auto mb-12 sm:mb-16">
      <h2 class="text-2xl xs:text-3xl sm:text-4xl md:text-5xl font-extrabold mt-2 mb-3 sm:mb-4 text-slate-900 tracking-tight leading-snug sm:leading-tight">
        Lo que dominarás desde el <span class="bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 bg-clip-text text-transparent">Día 1</span> para facturar
      </h2>
      <p class="text-slate-600 text-sm sm:text-base md:text-lg leading-relaxed max-w-2xl mx-auto">
        Te preparamos con el stack tecnológico exacto que exigen hoy las empresas y los clientes mejor pagados del mercado digital.
      </p>
    </div>

    <!-- Grid responsive con columnas adaptables para móviles, tablets y escritorio -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
      
      <!-- Tarjeta 1: VS Code -->
      <div class="bg-[#f8fafc]/95 sm:bg-[#f8fafc] p-5 sm:p-6 rounded-2xl border border-slate-200 hover:border-blue-500/50 hover:bg-white transition-all duration-300 group shadow-lg shadow-black/5 backdrop-blur-sm">
        <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-blue-500/10 flex items-center justify-center mb-4 sm:mb-5 text-[#007ACC] group-hover:scale-110 transition-transform">
          <svg class="w-6 h-6 sm:w-7 sm:h-7" viewBox="0 0 24 24" fill="currentColor"><path d="M17.525 2.155a1.18 1.18 0 0 0-1.127.143l-9.67 6.446-4.14-3.312a1.18 1.18 0 0 0-1.745 1.05v11.336a1.18 1.18 0 0 0 1.745 1.05l4.14-3.312 9.67 6.446a1.18 1.18 0 0 0 1.795-.989V3.144a1.18 1.18 0 0 0-.668-.989zm-1.07 16.591L8.355 13.5l8.1-5.4v10.846z"/></svg>
        </div>
        <h3 class="text-base sm:text-lg font-bold text-slate-900 mb-1.5 sm:mb-2 group-hover:text-[#0071e3] transition-colors">Entorno Profesional</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Domina Visual Studio Code como un experto para escribir código limpio, blindado y ultrarrápido.</p>
      </div>

      <!-- Tarjeta 2: Git / GitHub -->
      <div class="bg-[#f8fafc]/95 sm:bg-[#f8fafc] p-5 sm:p-6 rounded-2xl border border-slate-200 hover:border-indigo-600/50 hover:bg-white transition-all duration-300 group shadow-lg shadow-black/5 backdrop-blur-sm">
        <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-indigo-600/10 flex items-center justify-center mb-4 sm:mb-5 text-indigo-600 group-hover:scale-110 transition-transform">
          <svg class="w-6 h-6 sm:w-7 sm:h-7" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
        </div>
        <h3 class="text-base sm:text-lg font-bold text-slate-900 mb-1.5 sm:mb-2 group-hover:text-indigo-600 transition-colors">Control de Versiones</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Gestiona proyectos con Git y GitHub a nivel corporativo, colaborando en equipos sin riesgo a errores.</p>
      </div>

      <!-- Tarjeta 3: NPM -->
      <div class="bg-[#f8fafc]/95 sm:bg-[#f8fafc] p-5 sm:p-6 rounded-2xl border border-slate-200 hover:border-sky-400/50 hover:bg-white transition-all duration-300 group shadow-lg shadow-black/5 backdrop-blur-sm">
        <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-sky-400/10 flex items-center justify-center mb-4 sm:mb-5 text-[#CB3837] group-hover:scale-110 transition-transform">
          <svg class="w-6 h-6 sm:w-7 sm:h-7" viewBox="0 0 24 24" fill="currentColor"><path d="M0 7.334v9.332h24V7.334H0zm3 2h3v5.332H4.334v-3.332H4v3.332H3V9.334zm5 0h3v5.332H9.334v-3.332H9v3.332H8V9.334zm6 0h4v5.332h-1V11.334h-2v3.332h-1V9.334zm-9 1v3.332h1V10.334H5zm5 0v3.332h1V10.334h-1z"/></svg>
        </div>
        <h3 class="text-base sm:text-lg font-bold text-slate-900 mb-1.5 sm:mb-2 group-hover:text-sky-500 transition-colors">Gestión de Paquetes</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Instala dependencias y domina NPM para acelerar entregas y optimizar flujos web modernos.</p>
      </div>

      <!-- Tarjeta 4: Asistentes de IA -->
      <div class="bg-[#f8fafc]/95 sm:bg-[#f8fafc] p-5 sm:p-6 rounded-2xl border border-slate-200 hover:border-[#0071e3]/50 hover:bg-white transition-all duration-300 group shadow-lg shadow-black/5 backdrop-blur-sm">
        <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-[#0071e3]/10 flex items-center justify-center mb-4 sm:mb-5 text-xl font-black group-hover:scale-110 transition-transform">
          🤖
        </div>
        <h3 class="text-base sm:text-lg font-bold text-slate-900 mb-1.5 sm:mb-2 group-hover:text-[#0071e3] transition-colors">Asistentes de IA</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Implementa Inteligencia Artificial para multiplicar x10 tu velocidad de desarrollo y acelerar tu monetización.</p>
      </div>

    </div>
  </div>
</section>
<!-- SECCIÓN 2: METODOLOGÍA Y NEGOCIO -->
<section class="bg-white text-slate-900 py-24 px-4 sm:px-6 lg:px-8 border-b border-blue-500/20 relative overflow-hidden">
  <!-- Efectos de luz ambiental de alta conversión -->
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[400px] bg-[#0071e3]/10 blur-[150px] rounded-full"></div>
  </div>

  <div class="max-w-[1150px] mx-auto bg-gradient-to-br from-[#f8fafc] via-white to-[#f8fafc] rounded-3xl p-8 sm:p-14 shadow-2xl shadow-blue-500/10 border border-blue-500/30 relative overflow-hidden z-10">
    <div class="absolute -top-32 -right-32 w-80 h-80 bg-[#0071e3]/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="grid grid-cols-1 md:grid-cols-12 gap-10 items-center relative z-10">
      
      <!-- Columna de Texto persuasivo -->
      <div class="md:col-span-7 space-y-6">
      
       
        
        <h2 class="text-3xl sm:text-5xl font-extrabold text-slate-900 tracking-tight leading-tight">
          Metodología 100% Práctica para <span class="bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 bg-clip-text text-transparent">Generar Ingresos</span>
        </h2>
        
        <p class="text-slate-600 text-base sm:text-lg leading-relaxed">
          No solo aprenderás a programar: te enseñamos el modelo de negocio exacto para conseguir tus primeros clientes, cobrar en dólares y facturar ofreciendo soluciones web profesionales optimizadas con IA.
        </p>

        <!-- Mini beneficios de autoridad -->
        <div class="grid grid-cols-2 gap-4 pt-2">
          <div class="flex items-center gap-2.5 text-xs sm:text-sm text-slate-700 font-medium">
            <svg class="w-5 h-5 text-[#0071e3] shrink-0" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
            <span>Clientes recurrentes</span>
          </div>
          <div class="flex items-center gap-2.5 text-xs sm:text-sm text-slate-700 font-medium">
            <svg class="w-5 h-5 text-[#0071e3] shrink-0" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
            <span>Cobros en moneda extranjera</span>
          </div>
        </div>
      </div>

      <!-- Columna de Acción (Tarjeta destacada) -->
      <div class="md:col-span-5 bg-white/90 backdrop-blur-xl p-6 sm:p-8 rounded-2xl border border-blue-500/30 text-center flex flex-col justify-between shadow-xl relative group hover:border-blue-500/60 transition-all">
        <div class="absolute inset-0 bg-gradient-to-b from-[#0071e3]/5 to-transparent rounded-2xl pointer-events-none"></div>

        <div class="relative z-10">
          <span class="inline-block text-[11px] uppercase tracking-wider font-extrabold text-[#0071e3] bg-[#0071e3]/10 px-3.5 py-1.5 rounded-full border border-[#0071e3]/30 mb-4">
            Alta Demanda Global
          </span>
          <div class="text-3xl sm:text-4xl font-black text-slate-900 mt-2 mb-2 tracking-tight">
            Acceso Inmediato
          </div>
          <p class="text-xs sm:text-sm text-slate-600 mb-8 leading-relaxed">
            Convierte cada desarrollo web en una fuente sólida y constante de ingresos.
          </p>
        </div>

        <a 
          href="#catalogo-cursos" 
          class="relative z-10 block w-full bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 hover:from-[#0066cc] hover:to-blue-500 text-white font-black text-sm sm:text-base py-4 px-6 rounded-xl transition-all shadow-lg shadow-blue-500/25 hover:shadow-blue-500/40 hover:-translate-y-0.5 text-center tracking-wide uppercase"
        >
          QUIERO EMPEZAR A GANAR
        </a>
      </div>

    </div>
  </div>
</section>

<!-- SECCIÓN 3: PERFILES IDEALES -->
<section class="bg-[#f8fafc] text-slate-900 py-20 px-4 sm:px-6 lg:px-8 border-b border-slate-200">
  <div class="max-w-[1100px] mx-auto">
    <div class="text-center max-w-3xl mx-auto mb-16">
      <h2 class="text-3xl sm:text-4xl font-extrabold text-slate-900 mb-4">¿Para quién es este programa?</h2>
      <p class="text-slate-600 text-sm sm:text-base">Diseñado para adaptarse a tus metas, sin importar tu nivel de experiencia previo.</p>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-3 gap-6 text-left">
      <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-lg shadow-black/5 hover:border-[#0071e3]/40 transition-all">
        <div class="text-3xl mb-4">🚀</div>
        <h3 class="font-extrabold text-[#0071e3] text-base mb-2 uppercase tracking-wider">Emprendedores</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Lanza tu propio negocio online al siguiente nivel, destaca frente a tu competencia y reduce costos operativos drásticamente sin depender de agencias externas.</p>
      </div>

      <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-lg shadow-black/5 hover:border-[#0071e3]/40 transition-all">
        <div class="text-3xl mb-4">💻</div>
        <h3 class="font-extrabold text-[#0071e3] text-base mb-2 uppercase tracking-wider">Freelancers</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Cobra por diseñar páginas web de alto impacto, automatiza entregas con IA y genera ingresos estables desde casa trabajando con clientes de todo el mundo.</p>
      </div>

      <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-lg shadow-black/5 hover:border-[#0071e3]/40 transition-all">
        <div class="text-3xl mb-4">🎓</div>
        <h3 class="font-extrabold text-[#0071e3] text-base mb-2 uppercase tracking-wider">Estudiantes</h3>
        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed">Domina desde cero la habilidad digital mejor pagada y más solicitada del mercado actual para construir un futuro financiero sólido e independiente.</p>
      </div>
    </div>
  </div>
</section>
<!-- SECCIÓN 4: DIFERENCIACIÓN (VS WORDPRESS / CLAUDE) -->
<section class="py-24 px-4 sm:px-6 lg:px-8 bg-white text-slate-900 font-sans border-b border-slate-200 relative overflow-hidden">
  <!-- Efectos de luz ambiental corporativos y de alto impacto -->
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[450px] bg-[radial-gradient(circle_at_center,rgba(0,113,227,0.08)_0%,transparent_70%)]"></div>
  </div>

  <div class="max-w-[1100px] mx-auto text-center relative z-10">
  
    <h2 class="text-3xl sm:text-5xl md:text-6xl font-black mb-6 tracking-tight text-slate-900 uppercase leading-[1.08]">
      ¿Por qué este curso es <span class="bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 bg-clip-text text-transparent inline-block drop-shadow-sm">diferente y superior</span> a WordPress o Claude?
    </h2>
    
    <p class="text-slate-600 text-base sm:text-lg md:text-xl max-w-3xl mx-auto mb-16 leading-relaxed font-normal">
      Olvídate de plataformas lentas, vulnerables o de copiar fragmentos de texto sueltos de inteligencias artificiales sin saber qué hacer con ellos para monetizar.
    </p>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left mb-16">
      <!-- Tarjeta 1: WordPress -->
      <div class="bg-[#f8fafc] p-8 rounded-3xl border border-slate-200 hover:border-rose-500/40 transition-all duration-300 shadow-xl shadow-black/5 flex flex-col justify-between group">
        <div>
          <div class="inline-block text-rose-600 font-extrabold text-[11px] uppercase tracking-wider bg-rose-500/10 px-3 py-1 rounded-full border border-rose-500/20 mb-4">
            ❌ El problema de WordPress
          </div>
          <h3 class="text-xl font-black mb-3 text-slate-900 group-hover:text-rose-600 transition-colors">Lento, costoso y propenso a hackeos</h3>
          <p class="text-slate-600 text-sm leading-relaxed mb-6">
            Plugins que se rompen, actualizaciones constantes, bases de datos pesadas y vulnerabilidades de seguridad que exponen tu negocio frente a la competencia.
          </p>
        </div>
        <div class="pt-4 border-t border-slate-200 text-emerald-600 text-xs font-bold flex items-center gap-1.5">
          <span>✓</span> Sitios web limpios, ligeros y blindados.
        </div>
      </div>

      <!-- Tarjeta 2: Claude / IA sin estructura -->
      <div class="bg-[#f8fafc] p-8 rounded-3xl border border-slate-200 hover:border-rose-500/40 transition-all duration-300 shadow-xl shadow-black/5 flex flex-col justify-between group">
        <div>
          <div class="inline-block text-rose-600 font-extrabold text-[11px] uppercase tracking-wider bg-rose-500/10 px-3 py-1 rounded-full border border-rose-500/20 mb-4">
            ❌ El límite de solo usar Claude
          </div>
          <h3 class="text-xl font-black mb-3 text-slate-900 group-hover:text-rose-600 transition-colors">Código suelto sin estructura real</h3>
          <p class="text-slate-600 text-sm leading-relaxed mb-6">
            Una IA te da bloques de código, pero si no sabes cómo integrarlos, gestionarlos ni subirlos a internet, te quedas atascado sin poder facturar.
          </p>
        </div>
        <div class="pt-4 border-t border-slate-200 text-emerald-600 text-xs font-bold flex items-center gap-1.5">
          <span>✓</span> Orquestación profesional de IA orientada a ventas.
        </div>
      </div>

      <!-- Tarjeta 3: El Stack del Futuro (Destacada) -->
      <div class="bg-gradient-to-br from-[#0071e3]/10 via-blue-600/5 to-white p-8 rounded-3xl border-2 border-[#0071e3]/40 shadow-2xl shadow-blue-500/10 flex flex-col justify-between relative overflow-hidden group">
        <div class="absolute top-0 right-0 bg-[#0071e3] text-white text-[10px] font-black uppercase px-4 py-1.5 rounded-bl-2xl tracking-wider shadow-sm">
          El Stack del Futuro
        </div>
        <div>
          <div class="inline-block text-[#0071e3] font-extrabold text-[11px] uppercase tracking-wider bg-[#0071e3]/10 px-3 py-1 rounded-full border border-[#0071e3]/20 mb-4">
            🚀 Nuestra Metodología
          </div>
          <h3 class="text-xl font-black mb-3 text-slate-900 group-hover:text-[#0071e3] transition-colors">Velocidad Extrema con VS Code, GitHub y Vercel</h3>
          <p class="text-slate-600 text-sm leading-relaxed mb-6">
            Construye en el entorno profesional más potente (<strong class="text-slate-900 font-bold">VS Code</strong>), protege tus cambios en la nube (<strong class="text-slate-900 font-bold">GitHub</strong>) y publícalo en vivo globalmente en segundos (<strong class="text-slate-900 font-bold">Vercel</strong>).
          </p>
        </div>
        <div class="pt-4 border-t border-blue-500/20 text-[#0071e3] text-xs font-black uppercase tracking-wider">
          ⚡ ¡Tu web en línea más rápido que nunca!
        </div>
      </div>
    </div>

    <!-- Caja de llamada a la acción final de alto impacto -->
    <div class="bg-gradient-to-br from-[#f8fafc] via-white to-[#f8fafc] p-10 rounded-3xl border border-blue-500/30 inline-block w-full max-w-4xl text-center shadow-2xl shadow-blue-500/10 relative overflow-hidden">
      <div class="absolute -top-24 -left-24 w-48 h-48 bg-[#0071e3]/10 rounded-full blur-2xl pointer-events-none"></div>
      
      <h3 class="text-2xl sm:text-3xl font-black mb-3 text-slate-900 tracking-tight">¿Listo para dominar la habilidad que genera ingresos reales?</h3>
      <p class="text-slate-600 text-sm sm:text-base mb-8 max-w-xl mx-auto">Elige tu plan a continuación y obtén acceso inmediato 24/7 a todos los módulos prácticos en video.</p>
      
      <a 
        href="#catalogo-cursos" 
        class="inline-flex items-center justify-center gap-3 bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 hover:from-[#0066cc] hover:to-blue-500 text-white font-black text-base px-10 py-5 rounded-2xl transition-all shadow-xl shadow-blue-500/25 hover:shadow-blue-500/40 hover:-translate-y-0.5 tracking-wider uppercase"
      >
        <span>ELEGIR MI CURSO AHORA</span>
        <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M19 14l-7 7m0 0l-7-7m7 7V3"/></svg>
      </a>
    </div>
  </div>
</section>

<!-- SECCIÓN 5: CATÁLOGO DE CURSOS CON CARRITO -->
<section id="catalogo-cursos" class="py-24 px-4 bg-white text-slate-900 font-sans border-b border-slate-200 relative overflow-hidden">
  <!-- Efectos de luz ambiental de alto rendimiento -->
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[450px] bg-[radial-gradient(circle_at_center,rgba(0,113,227,0.08)_0%,transparent_70%)]"></div>
  </div>

  <div class="max-w-[1200px] mx-auto text-center relative z-10">
  
    <h2 class="text-3xl md:text-5xl font-black mb-6 tracking-tight text-slate-900 uppercase">
      Elige tu nivel de formación
    </h2>
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal leading-relaxed">
      Selecciona el plan que mejor se adapte a tus metas y comienza a crear páginas web profesionales hoy mismo.
    </p>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-left items-stretch">
      
      <!-- Producto 1 -->
      <div class="bg-[#f8fafc] rounded-3xl p-8 border border-slate-200 shadow-xl shadow-black/5 hover:shadow-2xl hover:border-[#0071e3]/40 transition-all duration-300 flex flex-col justify-between group">
        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-950 mb-6 shadow-inner">
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
            <span class="absolute top-4 left-4 bg-[#0071e3] text-white text-[11px] font-extrabold uppercase tracking-wider px-3 py-1 rounded-full shadow-md">
              Más Popular
            </span>
          </div>

          <span class="text-xs font-bold text-[#0071e3] uppercase tracking-wider">Acceso Grabado</span>
          <h3 class="text-2xl font-black mt-1 mb-2 text-slate-900">Paquete Solo Videos</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Ideal para estudiantes independientes, autodidactas o personas con presupuesto ajustado que prefieren aprender a su propio ritmo.
          </p>

          <div class="space-y-2 mb-8 text-sm text-slate-700 border-t border-slate-200 pt-4 font-medium">
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Acceso ilimitado a las lecciones en video grabadas</div>
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Código fuente de ejemplo y plantillas</div>
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Acceso a la comunidad de apoyo</div>
          </div>
        </div>

        <div>
          <div class="flex items-center justify-between mb-4 pt-4 border-t border-slate-200">
            <span class="text-xs text-slate-500 font-semibold">Inversión única</span>
            <span class="text-3xl font-black text-slate-900">$50 <span class="text-sm font-normal text-slate-500">USD</span></span>
          </div>

          <button 
            type="button"
            onclick={() => agregarAlCarrito('Paquete Solo Videos (Acceso Grabado)', 50, 'Curso')}
            class="w-full bg-white hover:bg-[#0071e3] text-slate-900 hover:text-white font-bold text-sm py-4 rounded-xl transition-all shadow-md flex items-center justify-center gap-2 cursor-pointer border border-slate-300 hover:border-[#0071e3]"
          >
            <span>Agregar al carrito</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
          </button>
        </div>
      </div>

      <!-- Producto 2 -->
      <div class="bg-[#f8fafc] rounded-3xl p-8 border border-slate-200 shadow-xl shadow-black/5 hover:shadow-2xl hover:border-amber-500/40 transition-all duration-300 flex flex-col justify-between group relative">
        <div class="absolute -top-3.5 right-6 bg-amber-500 text-slate-950 text-[11px] font-extrabold uppercase tracking-wider px-3.5 py-1 rounded-full shadow-md">
          Cupos Exclusivos
        </div>

        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-950 mb-6 shadow-inner">
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
            <span class="absolute top-4 left-4 bg-amber-500 text-slate-950 text-[11px] font-extrabold uppercase tracking-wider px-3 py-1 rounded-full shadow-md">
              VIP / Personalizado
            </span>
          </div>

          <span class="text-xs font-bold text-amber-600 uppercase tracking-wider">Acompañamiento Directo</span>
          <h3 class="text-2xl font-black mt-1 mb-2 text-slate-900">Videos + Mentoría 1 a 1</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Diseñado para acelerar tu curva de aprendizaje, resolver dudas técnicas específicas de inmediato y recibir retroalimentación directa sobre tus proyectos.
          </p>

          <div class="space-y-2 mb-8 text-sm text-slate-700 border-t border-slate-200 pt-4 font-medium">
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> Todo el contenido del Paquete Solo Videos</div>
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> Mentoría individual</div>
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> Revisión de código personalizada y soporte prioritario por chat</div>
          </div>
        </div>

        <div>
          <div class="flex items-center justify-between mb-4 pt-4 border-t border-slate-200">
            <span class="text-xs text-slate-500 font-semibold">Inversión única</span>
            <span class="text-3xl font-black text-slate-900">$150 <span class="text-sm font-normal text-slate-500">USD</span></span>
          </div>

          <button 
            type="button"
            onclick={() => agregarAlCarrito('Videos + Mentoría 1 a 1 (VIP)', 150, 'Mentoría')}
            class="w-full bg-gradient-to-r from-[#0071e3] via-blue-600 to-sky-500 hover:from-[#0066cc] hover:to-blue-500 text-white font-black text-sm py-4 rounded-xl transition-all shadow-lg shadow-blue-500/25 hover:shadow-blue-500/40 flex items-center justify-center gap-2 cursor-pointer"
          >
            <span>Agregar al carrito</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
          </button>
        </div>
      </div>

    </div>
  </div>
</section>