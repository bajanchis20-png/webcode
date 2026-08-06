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
    <div class="fixed top-20 right-6 z-50 bg-slate-900 text-white px-6 py-3 rounded-2xl shadow-2xl border border-white/20 flex items-center gap-3 animate-fade-in-down">
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
    <div class="fixed bottom-24 right-6 z-50 w-[350px] sm:w-[380px] bg-white rounded-3xl p-6 border border-slate-200 shadow-2xl text-left animate-fade-in-down">
        <div class="flex items-center justify-between pb-3 border-b border-slate-100 mb-4">
            <h3 class="text-base font-bold text-slate-900 flex items-center gap-2">
                <span>🛒 Tu Carrito</span>
                <span class="bg-blue-50 text-[#0066cc] text-xs px-2 py-0.5 rounded-full font-semibold">{carrito.length}</span>
            </h3>
            <button onclick={() => carritoAbierto = false} class="text-slate-400 hover:text-slate-700 text-sm font-semibold cursor-pointer">✕</button>
        </div>

        {#if carrito.length === 0}
            <p class="text-xs text-slate-500 text-center py-6">Tu carrito está vacío. Agrega un curso para comenzar.</p>
        {:else}
            <div class="space-y-3 mb-4 max-h-60 overflow-y-auto pr-1">
                {#each carrito as item, index}
                    <div class="flex items-center justify-between bg-slate-50 p-3 rounded-2xl border border-slate-200/60 text-xs">
                        <div>
                            <h4 class="font-bold text-slate-900">{item.titulo}</h4>
                            <span class="text-slate-500">${item.precio} USD</span>
                        </div>
                        <button onclick={() => eliminarDelCarrito(index)} class="text-rose-500 hover:text-rose-700 font-semibold p-1 cursor-pointer">Eliminar</button>
                    </div>
                {/each}
            </div>

            <div class="pt-3 border-t border-slate-100 space-y-3">
                <div class="flex items-center justify-between text-sm">
                    <span class="text-slate-600 font-medium">Total:</span>
                    <span class="text-lg font-extrabold text-slate-900">${calcularTotal()} USD</span>
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

<!-- Sección Hero / Educativa con alto impacto visual y CTA hacia el catálogo -->
<section class="bg-white text-slate-900 pt-16 sm:pt-24 md:pt-28 pb-20 sm:pb-24 px-4 sm:px-6 lg:px-8 text-center font-sans relative overflow-hidden border-b border-slate-200">
  
  <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
    <div class="absolute inset-0 bg-gradient-to-b from-white/90 via-white/80 to-white"></div>
  </div>

  <div class="absolute top-12 left-1/2 -translate-x-1/2 w-[280px] sm:w-[500px] md:w-[650px] h-[160px] sm:h-[300px] md:h-[380px] bg-gradient-to-tr from-[#0071e3]/15 to-sky-400/15 blur-[100px] sm:blur-[140px] md:blur-[160px] pointer-events-none rounded-full z-1"></div>

  <div class="max-w-[1100px] mx-auto flex flex-col items-center relative z-10 w-full">
    
   

    <h1 class="text-3xl xs:text-4xl sm:text-5xl md:text-6xl font-extrabold tracking-tight text-slate-900 mb-6 leading-[1.12] max-w-5xl uppercase">
    <br class="hidden sm:inline" />
      <span class="bg-gradient-to-r from-[#0066cc] via-sky-600 to-indigo-600 bg-clip-text text-transparent inline-block mt-2">Crea páginas web profesionales y gana dinero real haciéndolo.</span>
    </h1>

    <p class="text-base sm:text-lg md:text-xl font-medium text-slate-600 max-w-2xl mb-10 leading-relaxed">
      Domina herramientas modernas, automatiza procesos con Inteligencia Artificial y conviértete en un creador web altamente cotizado en el mercado digital.
    </p>

    <!-- Botón con llamada directa al catálogo -->
    <div class="mb-14">
      <a 
        href="#catalogo-cursos" 
        class="inline-flex items-center gap-2 bg-[#0071e3] hover:bg-[#0077ed] text-white font-bold text-base px-9 py-4 rounded-2xl transition-all shadow-xl shadow-blue-500/25 hover:scale-105"
      >
        <span>VER CURSOS Y EMPEZAR A GANAR</span>
        <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M19 14l-7 7m0 0l-7-7m7 7V3"/></svg>
      </a>
    </div>

    <!-- Tarjeta Informativa Principal Altamente Llamativa y Expandida -->
    <div class="w-full max-w-5xl bg-gradient-to-br from-[#084556] via-[#063340] to-[#04222b] rounded-3xl p-8 sm:p-12 text-white text-left shadow-2xl border border-white/10 mb-6 relative overflow-hidden">
      
      <div class="absolute -top-24 -right-24 w-64 h-64 bg-sky-400/10 rounded-full blur-3xl pointer-events-none"></div>

      <div class="grid grid-cols-1 md:grid-cols-12 gap-10 items-center relative z-10">
        
        <div class="md:col-span-7 space-y-6">
          <div>
            <span class="text-xs font-bold text-amber-300 uppercase tracking-widest bg-amber-400/15 px-3.5 py-1.5 rounded-lg border border-amber-400/30">🔥 La Ruta Hacia Tu Libertad Financiera</span>
            <h3 class="text-3xl sm:text-4xl font-extrabold mt-3 mb-3 text-white">Metodología 100% Práctica para Generar Ingresos</h3>
            <p class="text-slate-200 text-sm sm:text-base leading-relaxed font-normal">
              No solo aprenderás a programar: te enseñamos el modelo de negocio exacto para conseguir tus primeros clientes, cobrar en dólares y facturar ofreciendo soluciones web profesionales optimizadas con IA.
            </p>
          </div>

          <div>
            <h4 class="text-xs font-extrabold text-sky-300 uppercase tracking-wider mb-3">Lo que dominarás desde el Día 1:</h4>
            <ul class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs sm:text-sm text-slate-100 font-medium">
              <li class="flex items-center gap-2.5 bg-white/5 p-3 rounded-xl border border-white/10"><span class="text-amber-300 font-bold">✓</span> Entorno Profesional (VS Code)</li>
              <li class="flex items-center gap-2.5 bg-white/5 p-3 rounded-xl border border-white/10"><span class="text-amber-300 font-bold">✓</span> Control de Versiones (GitHub)</li>
              <li class="flex items-center gap-2.5 bg-white/5 p-3 rounded-xl border border-white/10"><span class="text-amber-300 font-bold">✓</span> Despliegue Instantáneo (Vercel)</li>
              <li class="flex items-center gap-2.5 bg-white/5 p-3 rounded-xl border border-white/10"><span class="text-amber-300 font-bold">✓</span> Asistentes de IA (Monetización rápida)</li>
            </ul>
          </div>
        </div>

        <div class="md:col-span-5 bg-white/10 backdrop-blur-md p-6 sm:p-8 rounded-2xl border border-white/20 text-center flex flex-col justify-between shadow-lg">
          <div>
            <span class="text-[11px] uppercase tracking-wider font-extrabold text-amber-300 bg-amber-400/20 px-3 py-1 rounded-full border border-amber-400/30">⚡ Alta Demanda Global</span>
            <div class="text-3xl sm:text-4xl font-black text-white mt-4 mb-1 tracking-tight">Acceso Inmediato</div>
            <p class="text-xs text-slate-200 mb-6">Convierte cada web en una fuente de ingresos recurrente</p>
          </div>

          <a 
            href="#catalogo-cursos" 
            class="block w-full bg-[#f49f54] hover:bg-[#e38d43] text-slate-900 font-black text-sm sm:text-base py-4 rounded-xl transition-all shadow-xl text-center tracking-wide"
          >
            QUIERO EMPEZAR A GANAR
          </a>
        </div>

      </div>

      <!-- Cuadros de Perfiles Ideales -->
      <div class="mt-10 pt-8 border-t border-white/15 grid grid-cols-1 sm:grid-cols-3 gap-4 text-center">
        <div class="bg-black/30 p-5 rounded-2xl border border-white/10 backdrop-blur-sm">
          <div class="font-extrabold text-amber-300 text-sm mb-1 uppercase tracking-wider">🚀 EMPRENDEDORES</div>
          <p class="text-xs text-slate-200">Lanza tu negocio online y reduce costos operativos drásticamente.</p>
        </div>
        <div class="bg-black/30 p-5 rounded-2xl border border-white/10 backdrop-blur-sm">
          <div class="font-extrabold text-amber-300 text-sm mb-1 uppercase tracking-wider">💻 FREELANCERS</div>
          <p class="text-xs text-slate-200">Cobra por diseñar páginas web y genera ingresos desde casa.</p>
        </div>
        <div class="bg-black/30 p-5 rounded-2xl border border-white/10 backdrop-blur-sm">
          <div class="font-extrabold text-amber-300 text-sm mb-1 uppercase tracking-wider">🎓 ESTUDIANTES</div>
          <p class="text-xs text-slate-200">Domina la habilidad digital mejor pagada del mercado actual.</p>
        </div>
      </div>

    </div>

  </div>
</section>

<!-- NUEVA SECCIÓN: ¿Por qué este curso y en qué nos diferenciamos de WordPress o Claude? -->
<section class="py-20 px-4 sm:px-6 lg:px-8 bg-slate-900 text-white font-sans border-b border-slate-800">
  <div class="max-w-[1100px] mx-auto text-center">
    
    <div class="inline-block px-4 py-1.5 bg-sky-500/15 text-sky-400 text-xs font-bold uppercase tracking-wider rounded-full mb-4 border border-sky-500/30">
      ⚡ Revolución Tecnológica
    </div>

    <h2 class="text-3xl md:text-5xl font-extrabold mb-4 tracking-tight">
      ¿Por qué este curso es <span class="text-sky-400">diferente y superior</span> a WordPress o Claude?
    </h2>
    <p class="text-slate-400 text-base md:text-lg max-w-2xl mx-auto mb-16">
      Olvídate de plataformas lentas, vulnerables o de copiar fragmentos de texto sueltos de inteligencias artificiales sin saber qué hacer con ellos.
    </p>

    <!-- Comparativa / Tarjetas de valor -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-left mb-16">
      
      <!-- Vs WordPress -->
      <div class="bg-slate-800/60 p-8 rounded-3xl border border-slate-700/60 backdrop-blur-sm flex flex-col justify-between">
        <div>
          <div class="text-rose-400 font-bold text-xs uppercase tracking-wider mb-2">❌ El problema de WordPress</div>
          <h3 class="text-xl font-bold mb-4 text-white">Lento, costoso y propenso a hackeos</h3>
          <p class="text-slate-300 text-sm leading-relaxed mb-6">
            Plugins que se rompen, actualizaciones constantes, bases de datos pesadas y vulnerabilidades de seguridad que exponen tu negocio.
          </p>
        </div>
        <div class="pt-4 border-t border-slate-700 text-emerald-400 text-xs font-bold">
          ✓ Nuestra solución: Sitios web limpios, ligeros y blindados.
        </div>
      </div>

      <!-- Vs Claude / IA Tradicional -->
      <div class="bg-slate-800/60 p-8 rounded-3xl border border-slate-700/60 backdrop-blur-sm flex flex-col justify-between">
        <div>
          <div class="text-rose-400 font-bold text-xs uppercase tracking-wider mb-2">❌ El límite de solo usar Claude</div>
          <h3 class="text-xl font-bold mb-4 text-white">Código suelto sin estructura real</h3>
          <p class="text-slate-300 text-sm leading-relaxed mb-6">
            Una IA te da bloques de código, pero si no sabes cómo integrarlos, gestionarlos ni subirlos a internet, te quedas atascado sin poder vender.
          </p>
        </div>
        <div class="pt-4 border-t border-slate-700 text-emerald-400 text-xs font-bold">
          ✓ Nuestra solución: Te enseñamos a orquestar la IA como un profesional.
        </div>
      </div>

      <!-- El Stack Ganador -->
      <div class="bg-gradient-to-br from-[#0071e3]/20 via-sky-600/10 to-transparent p-8 rounded-3xl border border-sky-500/30 backdrop-blur-sm flex flex-col justify-between relative overflow-hidden">
        <div class="absolute top-0 right-0 bg-sky-500 text-slate-900 text-[10px] font-black uppercase px-3 py-1 rounded-bl-xl">
          El Stack del Futuro
        </div>
        <div>
          <div class="text-sky-400 font-bold text-xs uppercase tracking-wider mb-2">🚀 Nuestra Metodología</div>
          <h3 class="text-xl font-bold mb-4 text-white">Velocidad Extrema con VS Code, GitHub y Vercel</h3>
          <p class="text-slate-300 text-sm leading-relaxed mb-6">
            Construye en el entorno profesional más potente (<strong class="text-white">VS Code</strong>), guarda y protege tus cambios en la nube (<strong class="text-white">GitHub</strong>) y publícalo en vivo globalmente en segundos (<strong class="text-white">Vercel</strong>).
          </p>
        </div>
        <div class="pt-4 border-t border-sky-500/30 text-amber-300 text-xs font-black uppercase tracking-wide">
          ⚡ ¡Tu web en línea más rápido que nunca!
        </div>
      </div>

    </div>

    <!-- Llamado a la acción interno -->
    <div class="bg-slate-800/80 p-8 rounded-3xl border border-slate-700 inline-block w-full max-w-3xl text-center shadow-xl">
      <h3 class="text-xl sm:text-2xl font-extrabold mb-2 text-white">¿Listo para dominar la habilidad que genera ingresos?</h3>
      <p class="text-slate-400 text-sm mb-6">Elige tu plan a continuación y obtén acceso inmediato a todos los módulos en video.</p>
      <a 
        href="#catalogo-cursos" 
        class="inline-block bg-[#0071e3] hover:bg-[#0077ed] text-white font-bold text-sm px-8 py-3.5 rounded-xl transition-all shadow-lg hover:scale-105"
      >
        ELEGIR MI CURSO AHORA
      </a>
    </div>

  </div>
</section>

<!-- Sección de Catálogo de Cursos con Carrito Interactivo -->
<section id="catalogo-cursos" class="py-24 px-4 bg-[#f8fafc] text-slate-900 font-sans border-b border-slate-200">
  <div class="max-w-[1200px] mx-auto text-center">
    
    <div class="inline-block px-4 py-1.5 bg-blue-50 text-[#0066cc] text-xs font-bold uppercase tracking-wider rounded-full mb-4 border border-blue-100 shadow-sm">
      🛍️ Catálogo Oficial de Programas
    </div>

    <h2 class="text-3xl md:text-5xl font-extrabold mb-4 tracking-tight text-slate-900">
      Elige tu nivel de formación
    </h2>
    <p class="text-slate-600 text-base md:text-lg max-w-2xl mx-auto mb-16 font-normal">
      Selecciona el plan que mejor se adapte a tus metas y comienza a crear páginas web profesionales hoy mismo.
    </p>

    <!-- Grid de Tarjetas Tipo Catálogo con precios y videos -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-left items-stretch">
      
      <!-- Producto 1 -->
      <div class="bg-white rounded-3xl p-8 border border-slate-200 shadow-lg hover:shadow-2xl transition-all duration-300 flex flex-col justify-between group">
        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-900 mb-6 shadow-inner">
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
            <span class="absolute top-4 left-4 bg-[#0071e3] text-white text-[11px] font-bold uppercase tracking-wider px-3 py-1 rounded-full shadow-md">
              Más Popular
            </span>
          </div>

          <span class="text-xs font-bold text-[#0066cc] uppercase tracking-wider">Acceso Completo</span>
          <h3 class="text-2xl font-extrabold mt-1 mb-2 text-slate-900">Crea tu web con IA</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Videos completos paso a paso. Aprende a dominar el entorno profesional, herramientas modernas y asistentes inteligentes para lanzar tu web desde cero.
          </p>

          <div class="space-y-2 mb-8 text-sm text-slate-600 border-t border-slate-100 pt-4 font-medium">
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Módulos prácticos en video HD</div>
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Plantillas y recursos descargables</div>
            <div class="flex items-center gap-2"><span class="text-[#0071e3] font-bold">✓</span> Acceso ilimitado por 1 año</div>
          </div>
        </div>

        <div>
          <div class="flex items-center justify-between mb-4 pt-4 border-t border-slate-100">
            <span class="text-xs text-slate-500 font-semibold">Inversión única</span>
            <span class="text-3xl font-black text-slate-900">$100 <span class="text-sm font-normal text-slate-500">USD</span></span>
          </div>

          <button 
            type="button"
            onclick={() => agregarAlCarrito('Crea tu web con IA (Acceso Completo)', 100, 'Curso')}
            class="w-full bg-slate-900 hover:bg-[#0071e3] text-white font-bold text-sm py-4 rounded-xl transition-all shadow-md flex items-center justify-center gap-2 cursor-pointer"
          >
            <span>Agregar al carrito</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
          </button>
        </div>
      </div>

      <!-- Producto 2 -->
      <div class="bg-white rounded-3xl p-8 border border-slate-200 shadow-lg hover:shadow-2xl transition-all duration-300 flex flex-col justify-between group relative">
        <div class="absolute -top-3.5 right-6 bg-amber-500 text-slate-900 text-[11px] font-bold uppercase tracking-wider px-3.5 py-1 rounded-full shadow-md">
          Cupos Exclusivos
        </div>

        <div>
          <div class="relative w-full aspect-video rounded-2xl overflow-hidden bg-slate-900 mb-6 shadow-inner">
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
            <span class="absolute top-4 left-4 bg-amber-500 text-slate-900 text-[11px] font-bold uppercase tracking-wider px-3 py-1 rounded-full shadow-md">
              VIP / Personalizado
            </span>
          </div>

          <span class="text-xs font-bold text-amber-600 uppercase tracking-wider">Acompañamiento Directo</span>
          <h3 class="text-2xl font-extrabold mt-1 mb-2 text-slate-900">Mentoría 1 a 1 + Curso</h3>
          <p class="text-sm text-slate-600 mb-6 leading-relaxed">
            Incluye todo el curso completo más asesorías personalizadas en vivo para revisar tu proyecto, resolver dudas y garantizar tu éxito digital.
          </p>

          <div class="space-y-2 mb-8 text-sm text-slate-600 border-t border-slate-100 pt-4 font-medium">
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> Todo el contenido del curso completo</div>
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> 3 Sesiones de mentoría 1 a 1 por Zoom</div>
            <div class="flex items-center gap-2"><span class="text-amber-600 font-bold">✓</span> Revisión y soporte directo de tu web</div>
          </div>
        </div>

        <div>
          <div class="flex items-center justify-between mb-4 pt-4 border-t border-slate-100">
            <span class="text-xs text-slate-500 font-semibold">Inversión única</span>
            <span class="text-3xl font-black text-slate-900">$150 <span class="text-sm font-normal text-slate-500">USD</span></span>
          </div>

          <button 
            type="button"
            onclick={() => agregarAlCarrito('Mentoría 1 a 1 + Curso Completo', 150, 'Mentoría')}
            class="w-full bg-[#0071e3] hover:bg-[#0077ed] text-white font-bold text-sm py-4 rounded-xl transition-all shadow-md flex items-center justify-center gap-2 cursor-pointer"
          >
            <span>Agregar al carrito</span>
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
          </button>
        </div>
      </div>

    </div>

  </div>
</section>