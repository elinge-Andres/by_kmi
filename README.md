<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BY_KMI - Minidonuts</title>

  <!-- Bootstrap -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600&display=swap" rel="stylesheet">
  
  <!-- Font Awesome para íconos -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

  <!-- Estilos personalizados -->
  <style>
    :root {
      --primary: #ff4f87;
      --secondary: #ff9b00;
      --background: #faf6ff;
      --text-color: #333;
    }

    body {
      font-family: 'Fredoka', sans-serif;
      color: var(--text-color);
      background-image: url('fondo3.jpg');
      background-size: cover;
      background-attachment: fixed;
      background-position: center;
      background-repeat: no-repeat;
      min-height: 100vh;
    }

    .container, .modal-content, .carousel {
      background-color: rgba(255, 255, 255, 0.85);
      border-radius: 15px;
      padding: 20px;
      margin-bottom: 20px;
    }

    section {
      background-color: rgba(255, 255, 255, 0.8);
      border-radius: 15px;
      padding: 20px;
      margin: 20px 0;
    }
     .navbar {
      background-color: var(--primary);
    }
    

    .navbar-brand, .nav-link {
      color: rgb(2, 2, 2) !important;
      font-weight: 600;
    }

    .btn-custom {
      background-color: var(--secondary);
      color: white;
      border-radius: 30px;
      padding: 10px 20px;
      transition: all 0.3s ease;
      font-weight: bold;
      border: none;
    }

    .btn-custom:hover {
      background-color: var(--primary);
      transform: scale(1.05);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }

    .btn-success {
      background-color: #25D366;
      color: white;
      border-radius: 30px;
      padding: 10px 20px;
      transition: all 0.3s ease;
      font-weight: bold;
      border: none;
    }

    .btn-success:hover {
      background-color: #1ebe5b;
      transform: scale(1.05);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }

    .carousel-item img {
      width: auto;
      max-height: 300px;
      object-fit: contain;
      margin: 0 auto;
    }

    .producto {
      text-align: center;
      margin-bottom: 2rem;
    }

    .producto img {
      width: 100%;
      max-height: 200px;
      object-fit: cover;
      border-radius: 15px;
    }

    footer {
      background-color: var(--primary);
      color: white;
      padding: 20px 0;
      text-align: center;
    }
    
    .badge-carrito {
      font-size: 0.6rem;
      top: -5px;
      right: -5px;
    }
    /* Estilo para la imagen flotante */
    .bykni-flotante {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 120px;
      z-index: 99;
      transition: all 0.3s ease;
      filter: drop-shadow(0 2px 5px rgba(0,0,0,0.2));
    }

    .bykni-flotante:hover {
      transform: scale(1.1) rotate(-5deg);
    }

    /* Estilos para el sistema de autenticación */
    .dropdown-menu {
      background-color: rgba(255, 255, 255, 0.95);
      border: none;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .dropdown-item {
      color: var(--text-color) !important;
      transition: all 0.2s;
    }

    .dropdown-item:hover {
      background-color: var(--primary);
      color: white !important;
    }

    .user-logged {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .user-avatar {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background-color: var(--secondary);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
    }

    @media (max-width: 768px) {
      .bykni-flotante {
        width: 90px;
        bottom: 15px;
        right: 15px;
      }
    }  
  </style>
</head>

<body>

  <!-- NAVBAR -->
  <nav class="navbar navbar-expand-lg">
    <div class="container">
      <a class="navbar-brand" href="#">BY_KMI</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#productos">Productos</a></li>
          <li class="nav-item"><a class="nav-link" href="#nosotros">Nosotros</a></li>
          <li class="nav-item"><a class="nav-link" href="#contacto">Contacto</a></li>
          <li class="nav-item">
            <a class="nav-link" href="ventascoorporativas.html">Ventas Corporativas y Fechas Especiales</a>
          </li>
          
          <!-- Menú desplegable de cuenta -->
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown">
              <i class="fas fa-user"></i> Cuenta
            </a>
            <ul class="dropdown-menu dropdown-menu-end">
              <li><a class="dropdown-item" href="#" data-bs-toggle="modal" data-bs-target="#registroModal">Registrarse</a></li>
              <li><a class="dropdown-item" href="#" data-bs-toggle="modal" data-bs-target="#loginModal">Iniciar Sesión</a></li>
              <li><hr class="dropdown-divider"></li>
              <li><a class="dropdown-item d-none" href="#" id="logoutBtn">Cerrar Sesión</a></li>
            </ul>
          </li>
          
          <li class="nav-item">
            <button class="btn btn-light position-relative" onclick="mostrarCarrito()">
              <i class="fa fa-shopping-cart"></i>
              <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger badge-carrito" id="contadorCarrito">0</span>
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- BANNER / CAROUSEL -->
  <div id="carouselExample" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="Mini1.jpg" class="d-block" alt="Mini1">
      </div>
      <div class="carousel-item">
        <img src="Mini2.jpg" class="d-block" alt="Mini2">
      </div>
      <div class="carousel-item">
        <img src="Mini3.jpg" class="d-block" alt="Mini3">
      </div>
      <div class="carousel-item">
        <img src="ancheta1.jpeg" class="d-block" alt="ancheta1">
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Anterior</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Siguiente</span>
    </button>
  </div>

  <!-- SECCIÓN PRODUCTOS -->
  <section id="productos" class="container py-5">
    <h2 class="text-center mb-4">Nuestros Minidonuts</h2>
    <div class="row">
      <div class="col-md-4 producto">
        <img src="Mini7.jpeg" alt="Donut 1">
        <h5 class="mt-2">Clásico Azúcar</h5>
        <p><strong>$4.000</strong></p>
        <button class="btn btn-custom mt-2" data-bs-toggle="modal" data-bs-target="#productoModal1">Ver más</button>
      </div>
      <div class="col-md-4 producto">
        <img src="Mini8.jpeg" alt="Donut 2">
        <h5 class="mt-2">Chocolate y Chips</h5>
        <p><strong>$5.000</strong></p>
        <button class="btn btn-custom mt-2" data-bs-toggle="modal" data-bs-target="#productoModal2">Ver más</button>
      </div>
      <div class="col-md-4 producto">
        <img src="caja mini2.jpeg" alt="Donut 3">
        <h5 class="mt-2">Anchetas y Desayunos sorpresas</h5>
        <p><strong>$30.000</strong></p>
        <button class="btn btn-custom mt-2" data-bs-toggle="modal" data-bs-target="#productoModal3">Ver más</button>
      </div>
    </div>
  </section>

  <!-- Modal Carrito -->
  <div class="modal fade" id="carritoModal" tabindex="-1" aria-labelledby="carritoModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="carritoModalLabel">Tu carrito</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
        </div>
        <div class="modal-body" id="carritoContenido">
          <p class="text-muted">Tu carrito está vacío.</p>
        </div>
        <div class="modal-footer">
          <button class="btn btn-success" onclick="finalizarCompra()">Finalizar compra</button>
          <button class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        </div>
      </div>
    </div>
  </div>

  <!-- MODAL TOPPINGS -->
  <div class="modal fade" id="toppingsModal" tabindex="-1" aria-labelledby="toppingsModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="toppingsModalLabel">Selecciona tus Toppings</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
        </div>
        <div class="modal-body">
          <form>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="Oreo" id="toppingOreo">
              <label class="form-check-label" for="toppingOreo">Oreo</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="Maní" id="toppingMani">
              <label class="form-check-label" for="toppingMani">Maní</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="Gomitas" id="toppingGomitas">
              <label class="form-check-label" for="toppingGomitas">Gomitas</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="checkbox" value="M&M" id="toppingMM">
              <label class="form-check-label" for="toppingMM">M&M</label>
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom">Guardar</button>
        </div>
      </div>
    </div>
  </div>

  <!-- MODAL COLORES -->
  <div class="modal fade" id="coloresModal" tabindex="-1" aria-labelledby="coloresModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="coloresModalLabel">Selecciona un Color</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
        </div>
        <div class="modal-body">
          <form>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="color" id="colorAmarillo" value="Amarillo">
              <label class="form-check-label" for="colorAmarillo">Amarillo</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="color" id="colorAzul" value="Azul">
              <label class="form-check-label" for="colorAzul">Azul</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="color" id="colorMorado" value="Morado">
              <label class="form-check-label" for="colorMorado">Morado</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="color" id="colorVerde" value="Verde">
              <label class="form-check-label" for="colorVerde">Verde</label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="color" id="colorRojo" value="Rojo">
              <label class="form-check-label" for="colorRojo">Rojo</label>
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom">Guardar</button>
        </div>
      </div>
    </div>
  </div>

  <!-- SECCIÓN NOSOTROS -->
  <section id="nosotros" class="container py-5">
    <h2 class="text-center mb-4">Sobre Nosotros</h2>
    <p class="text-center">
      En BY_KMI Somo una tienda virtual que transformamos cada momento en una dulce experiencia inolvidable. Nuestros minidonuts artesanales están hechos con ingredientes seleccionados y un toque especial de amor. Sorprende tu paladar con sabores únicos, colores vibrantes y la posibilidad de personalizarlos como más te gusten. ¡Cada bocado es una celebración!
    </p>
    <div class="text-center mt-3">
      <span style="color: #ff69b4; font-weight: bold; font-size: 1.5rem;">HECHO CON AMOR</span>
    </div>
  </section>

  <!-- SECCIÓN CONTACTO -->
  <section id="contacto" class="container py-5">
    <h2 class="text-center mb-4">Contáctanos</h2>
    <div class="text-center">
      <p class="mt-3 fw-bold" style="color: #000000; font-size: 1.2rem;">
      ¿Te animas a endulzar tu día? Escríbenos, que lo hacemos realidad 😋💬🍩</p>

      <!-- Botón WhatsApp -->
      <a href="https://wa.me/573219437192" target="_blank" class="btn btn-success me-2">
        <i class="fab fa-whatsapp"></i> Escríbenos por WhatsApp
      </a>

      <!-- Botón Instagram -->
      <a href="https://www.instagram.com/by_kmii?igsh=a3J5ejBxaWI5OTQy" target="_blank" class="btn btn-custom me-2">
        <i class="fab fa-instagram"></i> Instagram
      </a>

      <!-- Botón TikTok -->
      <a href="https://www.tiktok.com/@by_kmii?_t=ZS-8vmHWyrOjFX&_r=1" target="_blank" class="btn btn-dark">
        <i class="fab fa-tiktok"></i> TikTok
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>&copy; 2025 BY_KMI. Todos los derechos reservados.</p>
    <p><a href="https://instagram.com/by_kmii" class="text-white">Síguenos en Instagram</a></p>
    <img src="Logoby.jpeg" alt="Bykni - Hecho con amor" class="bykni-flotante">
  </footer>

  <!-- Modal para el producto 1 -->
  <div class="modal fade" id="productoModal1" tabindex="-1" aria-labelledby="productoModalLabel1" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="productoModalLabel1">Clásico Azúcar</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
        </div>
        <div class="modal-body">
          <div id="carouselProducto1" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="clasicas1.jpeg" class="d-block w-100" alt="clasicas1">
              </div>
              <div class="carousel-item">
                <img src="Clasicas2.jpeg" class="d-block w-100" alt="Clasicas2">
              </div>
              <div class="carousel-item">
                <img src="Clasicas3.jpeg" class="d-block w-100" alt="Clasicas3">
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselProducto1" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Anterior</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselProducto1" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Siguiente</span>
            </button>
          </div>
          <p class="mt-3">Una deliciosa Minidonut cubierta con azúcar granulada. Ideal para los amantes de lo clásico.</p>
          <div class="mt-3">
            <label for="cantidad1" class="form-label">Cantidad:</label>
            <div class="input-group" style="max-width: 150px;">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad1', -1)">-</button>
              <input type="number" class="form-control text-center" id="cantidad1" value="1" min="1">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad1', 1)">+</button>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom" onclick="agregarAlCarrito(1, 'Clásico Azúcar', 3000, 'cantidad1')">Agregar al carrito</button>
          <span id="stock-1" class="ms-3 text-muted">Stock: 20</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal para el producto 2 -->
  <div class="modal fade" id="productoModal2" tabindex="-1" aria-labelledby="productoModalLabel2" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="productoModalLabel2">Chocolate y Chips</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
        </div>
        <div class="modal-body">
          <div id="carouselProducto2" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="Mini9.jpg" class="d-block w-100" alt="Imagen 1 de Chocolate y Chips">
              </div>
              <div class="carousel-item">
                <img src="Mini6.jpeg" class="d-block w-100" alt="Imagen 2 de Chocolate y Chips">
              </div>
              <div class="carousel-item">
                <img src="Mini4.jpg" class="d-block w-100" alt="Imagen 3 de Chocolate y Chips">
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselProducto2" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Anterior</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselProducto2" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Siguiente</span>
            </button>
          </div>
          <p class="mt-3">Un irresistible Minidonut de chocolate cubierto con chips crocantes. Perfecto para quienes disfrutan del sabor intenso y la textura crujiente en cada bocado.</p>
          <div class="mt-3">
            <label for="cantidad2" class="form-label">Cantidad:</label>
            <div class="input-group" style="max-width: 150px;">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad2', -1)">-</button>
              <input type="number" class="form-control text-center" id="cantidad2" value="1" min="1">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad2', 1)">+</button>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom" onclick="agregarAlCarrito(2, 'Chocolate y Chips', 5000, 'cantidad2')">Agregar al carrito</button>
          <span id="stock-2" class="ms-3 text-muted">Stock: 20</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal para el producto 3 -->
  <div class="modal fade" id="productoModal3" tabindex="-1" aria-labelledby="productoModalLabel3" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="productoModalLabel3">Anchetas y Desayunos sorpresas</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
        </div>
        <div class="modal-body">
          <div id="carouselProducto3" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="ancheta.jpeg" class="d-block w-100" alt="Imagen 1 de Anchetas y Desayunos sorpresas">
              </div>
              <div class="carousel-item">
                <img src="cajadulces2.jpeg" class="d-block w-100" alt="Imagen 2 de Anchetas y Desayunos sorpresas">
              </div>
              <div class="carousel-item">
                <img src="cajadulces3.jpeg" class="d-block w-100" alt="Imagen 3 de Anchetas y Desayunos sorpresas">
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselProducto3" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Anterior</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselProducto3" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Siguiente</span>
            </button>
          </div>
          <p class="mt-3">Sorprende con nuestras anchetas personalizadas, llenas de dulces, snacks y detalles únicos. Perfectas para cumpleaños, aniversarios o simplemente para demostrar cariño.</p>
          <div class="mt-3">
            <label for="cantidad3" class="form-label">Cantidad:</label>
            <div class="input-group" style="max-width: 150px;">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad3', -1)">-</button>
              <input type="number" class="form-control text-center" id="cantidad3" value="1" min="1">
              <button class="btn btn-outline-secondary" type="button" onclick="cambiarCantidad('cantidad3', 1)">+</button>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom" onclick="agregarAlCarrito(3, 'Anchetas y Desayunos sorpresas', 25000, 'cantidad3')">Agregar al carrito</button>
          <span id="stock-3" class="ms-3 text-muted">Stock: 20</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal de Registro -->
  <div class="modal fade" id="registroModal" tabindex="-1" aria-labelledby="registroModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="registroModalLabel">Registrarse</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form id="registroForm">
            <div class="mb-3">
              <label for="nombreRegistro" class="form-label">Nombre Completo</label>
              <input type="text" class="form-control" id="nombreRegistro" required>
            </div>
            <div class="mb-3">
              <label for="emailRegistro" class="form-label">Correo Electrónico</label>
              <input type="email" class="form-control" id="emailRegistro" required>
            </div>
            <div class="mb-3">
              <label for="passwordRegistro" class="form-label">Contraseña</label>
              <input type="password" class="form-control" id="passwordRegistro" required minlength="6">
            </div>
            <div class="mb-3">
              <label for="confirmPassword" class="form-label">Confirmar Contraseña</label>
              <input type="password" class="form-control" id="confirmPassword" required>
            </div>
            <div class="alert alert-danger d-none" id="registroError"></div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom" onclick="registrarUsuario()">Registrarse</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal de Inicio de Sesión -->
  <div class="modal fade" id="loginModal" tabindex="-1" aria-labelledby="loginModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="loginModalLabel">Iniciar Sesión</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form id="loginForm">
            <div class="mb-3">
              <label for="emailLogin" class="form-label">Correo Electrónico</label>
              <input type="email" class="form-control" id="emailLogin" required>
            </div>
            <div class="mb-3">
              <label for="passwordLogin" class="form-label">Contraseña</label>
              <input type="password" class="form-control" id="passwordLogin" required>
            </div>
            <div class="alert alert-danger d-none" id="loginError"></div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
          <button type="button" class="btn btn-custom" onclick="iniciarSesion()">Iniciar Sesión</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal de Bienvenida -->
  <div class="modal fade" id="bienvenidaModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Bienvenido/a</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <p id="mensajeBienvenida"></p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-custom" data-bs-dismiss="modal">Continuar</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Scripts Bootstrap -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  
  <!-- Script del Carrito y Autenticación -->
  <script>
    // Variables globales
    let carrito = [];
    let contadorCarrito = 0;
    let usuarios = JSON.parse(localStorage.getItem('usuarios')) || [];
    let usuarioActual = JSON.parse(localStorage.getItem('usuarioActual')) || null;
    
    // Verificar si hay usuario logueado al cargar la página
    document.addEventListener('DOMContentLoaded', function() {
      actualizarEstadoLogin();
    });
    
    // Función para mostrar el carrito
    function mostrarCarrito() {
      const carritoModal = new bootstrap.Modal(document.getElementById('carritoModal'));
      actualizarContenidoCarrito();
      carritoModal.show();
    }
    
    // Función para agregar productos al carrito
    function agregarAlCarrito(id, nombre, precio, cantidadId) {
      const cantidad = parseInt(document.getElementById(cantidadId).value);
      const productoExistente = carrito.find(item => item.id === id);
      
      if (productoExistente) {
        productoExistente.cantidad += cantidad;
      } else {
        carrito.push({
          id: id,
          nombre: nombre,
          precio: precio,
          cantidad: cantidad
        });
      }
      
      // Actualizar contador
      contadorCarrito += cantidad;
      document.getElementById('contadorCarrito').textContent = contadorCarrito;
      
      // Mostrar notificación
      alert(`${nombre} agregado al carrito (${cantidad} unidades)`);
      
      // Cerrar el modal del producto
      const modal = bootstrap.Modal.getInstance(document.getElementById(`productoModal${id}`));
      modal.hide();
    }
    
    // Función para actualizar el contenido del carrito en el modal
    function actualizarContenidoCarrito() {
      const carritoContenido = document.getElementById('carritoContenido');
      
      if (carrito.length === 0) {
        carritoContenido.innerHTML = '<p class="text-muted">Tu carrito está vacío.</p>';
        return;
      }
      
      let html = '<table class="table">';
      html += '<thead><tr><th>Producto</th><th>Precio</th><th>Cantidad</th><th>Subtotal</th><th></th></tr></thead>';
      html += '<tbody>';
      
      let total = 0;
      
      carrito.forEach(item => {
        const subtotal = item.precio * item.cantidad;
        total += subtotal;
        
        html += `
          <tr>
            <td>${item.nombre}</td>
            <td>$${item.precio.toLocaleString()}</td>
            <td>${item.cantidad}</td>
            <td>$${subtotal.toLocaleString()}</td>
            <td><button class="btn btn-sm btn-danger" onclick="eliminarDelCarrito(${item.id})"><i class="fas fa-trash"></i></button></td>
          </tr>
        `;
      });
      
      html += '</tbody>';
      html += `<tfoot><tr><th colspan="3">Total</th><th>$${total.toLocaleString()}</th><th></th></tr></tfoot>`;
      html += '</table>';
      
      carritoContenido.innerHTML = html;
    }
    
    // Función para eliminar productos del carrito
    function eliminarDelCarrito(id) {
      const productoIndex = carrito.findIndex(item => item.id === id);
      
      if (productoIndex !== -1) {
        contadorCarrito -= carrito[productoIndex].cantidad;
        carrito.splice(productoIndex, 1);
        
        document.getElementById('contadorCarrito').textContent = contadorCarrito;
        actualizarContenidoCarrito();
      }
    }
    
    // Función para finalizar la compra
    function finalizarCompra() {
      if (carrito.length === 0) {
        alert('El carrito está vacío');
        return;
      }
      
      if (!usuarioActual) {
        alert('Por favor inicia sesión para completar tu compra');
        const loginModal = new bootstrap.Modal(document.getElementById('loginModal'));
        loginModal.show();
        return;
      }
      
      let mensaje = "¡Hola BY_KMI! Quisiera hacer un pedido con los siguientes productos:%0A%0A";
      carrito.forEach((producto, index) => {
        mensaje += `➡ ${producto.nombre}%0ACantidad: ${producto.cantidad}%0APrecio unitario: $${producto.precio.toLocaleString()}%0ASubtotal: $${(producto.precio * producto.cantidad).toLocaleString()}%0A%0A`;
      });

      const total = carrito.reduce((acc, p) => acc + p.precio * p.cantidad, 0);
      mensaje += `💰 *Total a pagar:* $${total.toLocaleString()}%0A%0A`;
      mensaje += "Por favor indíquenme los datos para realizar el pedido. ¡Gracias! 😊🍩";

      // Registrar el pedido en el historial del usuario
      const pedido = {
        id: Date.now(),
        fecha: new Date().toISOString(),
        productos: [...carrito],
        total,
        estado: 'pendiente'
      };

      usuarioActual.pedidos = usuarioActual.pedidos || [];
      usuarioActual.pedidos.push(pedido);
      
      // Actualizar el usuario en localStorage
      const usuarioIndex = usuarios.findIndex(u => u.id === usuarioActual.id);
      usuarios[usuarioIndex] = usuarioActual;
      localStorage.setItem('usuarios', JSON.stringify(usuarios));
      localStorage.setItem('usuarioActual', JSON.stringify(usuarioActual));

      const telefono = "573219437192";
      const url = `https://wa.me/${telefono}?text=${mensaje}`;

      // Limpiar carrito
      carrito = [];
      contadorCarrito = 0;
      document.getElementById('contadorCarrito').textContent = '0';
      actualizarContenidoCarrito();
      
      // Cerrar modal
      const carritoModal = bootstrap.Modal.getInstance(document.getElementById('carritoModal'));
      carritoModal.hide();
      
      // Abrir WhatsApp
      window.open(url, '_blank');
    }
    
    // Función para cambiar la cantidad
    function cambiarCantidad(inputId, cambio) {
      const input = document.getElementById(inputId);
      let cantidad = parseInt(input.value) || 1;
      cantidad += cambio;
      
      if (cantidad < 1) cantidad = 1;
      input.value = cantidad;
    }

    // Función para registrar un nuevo usuario
    function registrarUsuario() {
      const nombre = document.getElementById('nombreRegistro').value.trim();
      const email = document.getElementById('emailRegistro').value.trim();
      const password = document.getElementById('passwordRegistro').value;
      const confirmPassword = document.getElementById('confirmPassword').value;
      const errorElement = document.getElementById('registroError');

      // Validaciones
      if (password !== confirmPassword) {
        errorElement.textContent = 'Las contraseñas no coinciden';
        errorElement.classList.remove('d-none');
        return;
      }

      if (usuarios.some(u => u.email === email)) {
        errorElement.textContent = 'Este correo ya está registrado';
        errorElement.classList.remove('d-none');
        return;
      }

      // Crear nuevo usuario
      const nuevoUsuario = {
        id: Date.now(),
        nombre,
        email,
        password,
        fechaRegistro: new Date().toISOString(),
        pedidos: []
      };

      usuarios.push(nuevoUsuario);
      localStorage.setItem('usuarios', JSON.stringify(usuarios));

      // Iniciar sesión automáticamente
      usuarioActual = nuevoUsuario;
      localStorage.setItem('usuarioActual', JSON.stringify(usuarioActual));

      // Mostrar mensaje de éxito
      document.getElementById('mensajeBienvenida').textContent = `¡Bienvenido/a a BY_KMI, ${nombre}! Tu cuenta ha sido creada exitosamente.`;
      const bienvenidaModal = new bootstrap.Modal(document.getElementById('bienvenidaModal'));
      bienvenidaModal.show();

      // Cerrar modal de registro
      const registroModal = bootstrap.Modal.getInstance(document.getElementById('registroModal'));
      registroModal.hide();

      // Limpiar formulario
      document.getElementById('registroForm').reset();
      errorElement.classList.add('d-none');

      // Actualizar estado de login
      actualizarEstadoLogin();
    }

    // Función para iniciar sesión
    function iniciarSesion() {
      const email = document.getElementById('emailLogin').value.trim();
      const password = document.getElementById('passwordLogin').value;
      const errorElement = document.getElementById('loginError');

      const usuario = usuarios.find(u => u.email === email && u.password === password);

      if (!usuario) {
        errorElement.textContent = 'Correo o contraseña incorrectos';
        errorElement.classList.remove('d-none');
        return;
      }

      // Iniciar sesión
      usuarioActual = usuario;
      localStorage.setItem('usuarioActual', JSON.stringify(usuario));

      // Mostrar mensaje de bienvenida
      document.getElementById('mensajeBienvenida').textContent = `¡Bienvenido/a de vuelta, ${usuario.nombre}!`;
      const bienvenidaModal = new bootstrap.Modal(document.getElementById('bienvenidaModal'));
      bienvenidaModal.show();

      // Cerrar modal de login
      const loginModal = bootstrap.Modal.getInstance(document.getElementById('loginModal'));
      loginModal.hide();

      // Actualizar UI
      actualizarEstadoLogin();

      // Limpiar formulario
      document.getElementById('loginForm').reset();
      errorElement.classList.add('d-none');
    }

    // Función para cerrar sesión
    function cerrarSesion() {
      usuarioActual = null;
      localStorage.removeItem('usuarioActual');
      actualizarEstadoLogin();
      alert('Has cerrado sesión correctamente');
    }

    // Función para actualizar la UI según el estado de login
    function actualizarEstadoLogin() {
      const dropdownMenu = document.querySelector('.dropdown-menu');
      const logoutBtn = document.getElementById('logoutBtn');
      const dropdownToggle = document.querySelector('.dropdown-toggle');

      if (usuarioActual) {
        // Usuario logueado
        dropdownToggle.innerHTML = `
          <div class="user-logged">
            <div class="user-avatar">${usuarioActual.nombre.charAt(0).toUpperCase()}</div>
            <span>${usuarioActual.nombre.split(' ')[0]}</span>
          </div>
        `;
        logoutBtn.classList.remove('d-none');
      } else {
        // Usuario no logueado
        dropdownToggle.innerHTML = '<i class="fas fa-user"></i> Cuenta';
        logoutBtn.classList.add('d-none');
      }

      // Agregar evento al botón de cerrar sesión
      logoutBtn.onclick = cerrarSesion;
    }
  </script>
</body>
</html>
