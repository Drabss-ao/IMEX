<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Imex Jumar | Tecnología y Accesorios</title>
  <meta name="description" content="Venta de accesorios tecnológicos: USB, parlantes, audífonos, teclados, pilas y más. Envío rápido, atención personalizada, pagos seguros.">
  <meta name="keywords" content="Imex Jumar, tienda electrónica, tecnología, gadgets, parlantes, audífonos, USB, pilas, memorias, teclados">
  <link rel="icon" href="favicon.ico" type="image/x-icon">
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    let carrito = [];

    function agregarAlCarrito(nombre, precio) {
      carrito.push({ nombre, precio });
      actualizarVistaCarrito();
    }

    function actualizarVistaCarrito() {
      const carritoLista = document.getElementById('carrito-lista');
      if (!carritoLista) return;
      carritoLista.innerHTML = '';
      if (carrito.length === 0) {
        carritoLista.innerHTML = '<li class="italic">No hay productos aún.</li>';
        return;
      }
      carrito.forEach((item) => {
        const li = document.createElement('li');
        li.textContent = `${item.nombre} - $${item.precio.toFixed(2)}`;
        carritoLista.appendChild(li);
      });
    }

    function enviarPorWhatsApp() {
      if (carrito.length === 0) {
        alert("El carrito está vacío");
        return;
      }
      let mensaje = 'Hola, quiero hacer un pedido:\n';
      let total = 0;
      carrito.forEach(item => {
        mensaje += `- ${item.nombre} - $${item.precio.toFixed(2)}\n`;
        total += item.precio;
      });
      mensaje += `\nTotal: $${total.toFixed(2)}`;

      const telefono = '51941265794';
      const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
      window.open(url, '_blank');
    }

    function enviarFormulario(event) {
      event.preventDefault();
      const nombre = document.getElementById('nombre')?.value;
      const email = document.getElementById('email')?.value;
      const mensaje = document.getElementById('mensaje')?.value;

      const mailto = `mailto:tiendaelectronica@email.com?subject=Mensaje de ${encodeURIComponent(nombre)}&body=${encodeURIComponent(mensaje)}%0A%0AEmail de contacto: ${encodeURIComponent(email)}`;
      window.location.href = mailto;
    }

    let bannerIndex = 0;
    const banners = [
      'https://images.unsplash.com/photo-1587829741301-dc798b82b5f4?auto=format&fit=crop&w=1500&q=80',
      'https://images.unsplash.com/photo-1517059224940-d4af9eec41e5?auto=format&fit=crop&w=1500&q=80',
      'https://images.unsplash.com/photo-1539874754764-5a9655913c1e?auto=format&fit=crop&w=1500&q=80'
    ];

    function rotarBanner() {
      const banner = document.getElementById('banner-img');
      if (!banner) return;
      bannerIndex = (bannerIndex + 1) % banners.length;
      banner.src = banners[bannerIndex];
    }

    window.onload = () => {
      setInterval(rotarBanner, 4000);
    };
  </script>
</head>
<body class="bg-gradient-to-br from-blue-50 via-gray-100 to-blue-100 text-gray-800">
  <header class="bg-gradient-to-r from-blue-800 to-blue-600 text-white p-8 text-center shadow-lg">
    <div class="flex items-center justify-center mb-4">
      <img src="https://cdn-icons-png.flaticon.com/512/906/906343.png" alt="Logo" class="w-12 h-12 mr-3">
      <h1 class="text-4xl font-bold">Imex Jumar</h1>
    </div>
    <p class="text-lg">Tecnología confiable a tu alcance</p>
  </header>

  <nav class="bg-blue-700 text-white flex justify-center space-x-10 py-4 text-lg font-medium shadow-md">
    <a href="#inicio" class="hover:text-gray-300">Inicio</a>
    <a href="#productos" class="hover:text-gray-300">Productos</a>
    <a href="#carrito" class="hover:text-gray-300">Carrito</a>
    <a href="#testimonios" class="hover:text-gray-300">Opiniones</a>
    <a href="#contacto" class="hover:text-gray-300">Contacto</a>
  </nav>

  <section class="my-10 max-w-6xl mx-auto">
    <div class="overflow-hidden rounded-xl shadow-lg">
      <div class="w-full overflow-hidden">
        <img id="banner-img" src="https://images.unsplash.com/photo-1587829741301-dc798b82b5f4?auto=format&fit=crop&w=1500&q=80" class="w-full h-80 object-cover transition duration-500" alt="Banner principal">
      </div>
    </div>
  </section>

  <section id="productos" class="max-w-6xl mx-auto px-4 pb-12">
    <h2 class="text-3xl font-bold text-center text-blue-800 mb-8">Productos Destacados</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <div class="bg-white shadow-lg rounded-lg p-4">
        <h3 class="text-xl font-semibold mb-2">Memoria USB 32GB</h3>
        <p class="mb-2">Alta velocidad, ideal para documentos y fotos.</p>
        <p class="font-bold mb-2">S/ 25.00</p>
        <button onclick="agregarAlCarrito('USB 32GB', 25)" class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Agregar</button>
      </div>
      <div class="bg-white shadow-lg rounded-lg p-4">
        <h3 class="text-xl font-semibold mb-2">Audífonos Bluetooth</h3>
        <p class="mb-2">Cómodos y con excelente calidad de sonido.</p>
        <p class="font-bold mb-2">S/ 60.00</p>
        <button onclick="agregarAlCarrito('Audífonos Bluetooth', 60)" class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Agregar</button>
      </div>
    </div>
  </section>

  <section id="carrito" class="bg-gray-100 py-8">
    <div class="max-w-4xl mx-auto px-4">
      <h2 class="text-2xl font-bold text-center mb-4">Carrito</h2>
      <ul id="carrito-lista" class="list-disc list-inside space-y-2"></ul>
      <div class="mt-4 text-center">
        <button onclick="enviarPorWhatsApp()" class="bg-green-500 text-white px-6 py-2 rounded hover:bg-green-600">Enviar pedido por WhatsApp</button>
      </div>
    </div>
  </section>

</body>
</html>

