<html lang="es"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Jardín Infantil - Perfil</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600&display=swap');

    body {
      font-family: 'Fredoka', sans-serif;
      background: linear-gradient(to bottom, #fff0f5, #fce4ec);
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      overflow-x: hidden;
    }
    .container {
      position: relative;
      width: 95%;
      max-width: 420px;
      background: #ffffff;
      padding: 2rem;
      border-radius: 24px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
      border: 3px solid #f8bbd0;
      box-sizing: border-box;
    }
    h2 {
      text-align: center;
      color: #ec407a;
      margin-bottom: 1.5rem;
    }
    input, textarea {
      width: 100%;
      padding: 0.8rem;
      margin: 0.5rem 0;
      border: 1px solid #f8bbd0;
      border-radius: 12px;
      background: #fffafc;
      font-size: 1rem;
      box-sizing: border-box;
    }
    button {
      width: 100%;
      padding: 0.9rem;
      background: #f48fb1;
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-weight: bold;
      font-size: 1rem;
      transition: background 0.3s ease;
      margin-top: 0.5rem;
    }
    button:hover {
      background: #ec407a;
    }
    .perfil {
      display: none;
      flex-direction: column;
      align-items: center;
      color: #5b4a50;
      position: relative;
      padding-top: 2rem;
    }
    .perfil img {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      margin-bottom: 1rem;
      border: 3px solid #f8bbd0;
      object-fit: cover;
    }
    .perfil h3 {
      color: #ec407a;
      margin: 0.2rem 0;
    }
    .info-nino {
      text-align: center;
      margin-bottom: 0.7rem;
    }
    .info-nino p {
      margin: 0.3rem 0;
    }
    #alergias {
      margin-top: 0.3rem;
      font-style: italic;
      color: #b36c86;
    }
    #calendar {
      width: 100%;
      margin-top: 1rem;
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 5px;
    }
    .day {
      text-align: center;
      padding: 0.6rem;
      border-radius: 8px;
      background: #ffe6eb;
      font-size: 0.9rem;
    }
    .present {
      background-color: #c8e6c9;
    }
    .absent {
      background-color: #ffcdd2;
    }
    .editable {
      display: none;
      flex-direction: column;
      margin-top: 1rem;
    }
    /* Botón pequeño editar en esquina superior derecha */
    #btnEditar {
      position: absolute;
      top: 12px;
      right: 12px;
      background: #f48fb1;
      border: none;
      border-radius: 50%;
      width: 36px;
      height: 36px;
      cursor: pointer;
      color: white;
      font-size: 20px;
      line-height: 36px;
      text-align: center;
      transition: background 0.3s ease;
      z-index: 10;
    }
    #btnEditar:hover {
      background: #ec407a;
    }
    /* Botón mapa */
    #btnMapa {
      margin-top: 1.5rem;
      background: #f06292;
    }
    #btnMapa:hover {
      background: #d81b60;
    }
    #mapa {
      width: 100%;
      height: 240px;
      margin-top: 1rem;
      border-radius: 12px;
      display: none;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    /* Botón salida */
    #btnSalida {
      margin-top: 1rem;
      background: #ba68c8;
    }
    #btnSalida:hover {
      background: #8e24aa;
    }
    /* Botón notificaciones esquina superior izquierda */
    #btnNotificaciones {
      position: absolute;
      top: 12px;
      left: 12px;
      background: #f48fb1;
      border: none;
      border-radius: 50%;
      width: 36px;
      height: 36px;
      cursor: pointer;
      color: white;
      font-size: 20px;
      line-height: 36px;
      text-align: center;
      transition: background 0.3s ease;
      z-index: 10;
    }
    #btnNotificaciones:hover {
      background: #ec407a;
    }
    /* Panel notificaciones */
    #panelNotificaciones {
      position: fixed;
      top: 60px;
      left: 12px;
      width: 300px;
      max-width: 90vw;
      max-height: 400px;
      background: #fff0f4;
      border: 3px solid #f8bbd0;
      border-radius: 16px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      padding: 1rem;
      overflow-y: auto;
      display: none;
      z-index: 100;
    }
    #panelNotificaciones h4 {
      margin-top: 0;
      margin-bottom: 0.7rem;
      color: #ec407a;
      text-align: center;
    }
    #panelNotificaciones ul {
      list-style: none;
      padding-left: 0;
      margin: 0;
      max-height: 340px;
      overflow-y: auto;
    }
    #panelNotificaciones ul li {
      background: #fce4ec;
      margin-bottom: 8px;
      padding: 8px 12px;
      border-radius: 12px;
      color: #5b4a50;
      font-size: 0.9rem;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    /* QR code modal */
    #modalQR {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.25);
      padding: 1rem;
      display: none;
      z-index: 200;
      text-align: center;
      max-width: 90vw;
    }
    #modalQR canvas {
      margin: 0 auto;
      display: block;
      width: 200px;
      height: 200px;
    }
    #modalQR button {
      margin-top: 1rem;
      width: auto;
      padding: 0.5rem 1rem;
      background: #ec407a;
      font-size: 1rem;
      border-radius: 12px;
    }
    /* Botón QR en esquina superior derecha */
    #btnQR {
      position: absolute;
      top: 12px;
      right: 60px; /* un poco a la izquierda del btnEditar */
      background: #f48fb1;
      border: none;
      border-radius: 50%;
      width: 36px;
      height: 36px;
      cursor: pointer;
      color: white;
      font-size: 20px;
      line-height: 36px;
      text-align: center;
      transition: background 0.3s ease;
      z-index: 10;
    }
    #btnQR:hover {
      background: #ec407a;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="login">
      <h2>Ingreso al Jardín 🌼</h2>
      <input type="email" id="email" placeholder="Correo electrónico">
      <input type="password" id="password" placeholder="Contraseña">
      <button onclick="iniciarSesion()">Ingresar</button>
    </div>

   <div class="perfil">
      <button id="btnNotificaciones" title="Notificaciones" onclick="toggleNotificaciones()">🔔</button>
      <button id="btnQR" title="Mostrar Código QR" onclick="mostrarQR()">
        📱
      </button>
      <button id="btnEditar" title="Editar perfil" onclick="toggleEditar()">✏️</button>
      <img id="fotoNiña" src="https://i.postimg.cc/sxg8sbzZ/Chat-GPT-Image-18-jun-2025-14-30-03.png" alt="Foto niña">
      <div class="info-nino">
        <h3 contenteditable="false" id="nombreNiña">María Ovalle</h3>
        <p><strong>Edad:</strong> <span id="edad">4 años</span></p>
        <p><strong>Grupo:</strong> <span id="grupo">Medio Mayor A</span></p>
        <p><strong>Alergias:</strong> <span id="alergias">Ninguna registrada</span></p>
      </div>

  <div class="editable" id="formEditar">
        <input id="inputNombre" type="text" placeholder="Nombre">
        <input id="inputEdad" type="text" placeholder="Edad">
        <input id="inputGrupo" type="text" placeholder="Grupo">
        <textarea id="inputAlergias" placeholder="Alergias"></textarea>
        <button onclick="guardarCambios()">Guardar</button>
  </div>

   <h4>Asistencia (junio 2025)</h4>
  <div id="calendar"></div>
      <p id="porcentajeAsistencia"></p>    <h4>Persona autorizada para el retiro</h4>
   <p><strong>Nombre:</strong> Pablo Ovalle</p>
   <p><strong>RUT:</strong> 12.345.678-9</p>
   <p><strong>Relación:</strong> Padre</p>

   <button id="btnMapa" onclick="toggleMapa()">Mostrar mapa ubicación</button>
   <iframe id="mapa" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3329.594054479448!2d-70.64282268479243!3d-33.44534035519752!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9662c6c0d3b1f77f%3A0x5dbb76f39a0b2c03!2sJard%C3%ADn%20Infantil%20La%20Reina!5e0!3m2!1ses!2scl!4v1687099324950!5m2!1ses!2scl" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>

   <button id="btnSalida" onclick="marcarSalida()">Marcar salida</button>
  </div>
  </div>

  <!-- Panel de notificaciones -->
  <div id="panelNotificaciones">
    <h4>Notificaciones</h4>
    <ul id="listaNotificaciones"></ul>
  </div>

  <!-- Modal QR -->
  <div id="modalQR">
    <h4>Código QR del niño</h4>
    <canvas id="canvasQR"></canvas>
    <button onclick="cerrarQR()">Cerrar</button>
  </div>

  <!-- Librería QR -->
  <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>

  <script>
    const diasAsistencia = {
      1: true,
      2: true,
      3: false,
      4: true,
      5: true,
      6: false,
      7: true,
      8: true,
      9: false,
    };

    const notificaciones = [];

    function solicitarPermisoNotificacion() {
      if (!("Notification" in window)) {
        alert("Tu navegador no soporta notificaciones.");
        return false;
      }
      if (Notification.permission === "granted") {
        return true;
      } else if (Notification.permission !== "denied") {
        Notification.requestPermission().then((permission) => {
          if (permission === "granted") {
            alert("Permiso para notificaciones concedido.");
          } else {
            alert("No se concedió permiso para notificaciones.");
          }
        });
      }
      return Notification.permission === "granted";
    }

    function mostrarNotificacion(titulo, cuerpo) {
      if (Notification.permission === "granted") {
        new Notification(titulo, {
          body: cuerpo,
          icon: "https://i.postimg.cc/sxg8sbzZ/Chat-GPT-Image-18-jun-2025-14-30-03.png",
        });
      }
    }

    function agregarNotificacion(texto) {
      const fecha = new Date();
      notificaciones.unshift(
        `${fecha.toLocaleDateString()} ${fecha.toLocaleTimeString()} - ${texto}`
      );
      actualizarListaNotificaciones();
    }

    function actualizarListaNotificaciones() {
      const lista = document.getElementById("listaNotificaciones");
      lista.innerHTML = "";
      for (const nota of notificaciones) {
        const li = document.createElement("li");
        li.textContent = nota;
        lista.appendChild(li);
      }
    }

    function iniciarSesion() {
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;
      if (email === "apoderado@jardin.cl" && password === "1234") {
        document.querySelector(".login").style.display = "none";
        document.querySelector(".perfil").style.display = "flex";
        generarCalendario();

        if (solicitarPermisoNotificacion()) {
          mostrarNotificacion("Ingreso Jardín", "Tu hijo ingresó al jardín.");
        }
        agregarNotificacion("Tu hijo ingresó al jardín.");
      } else {
        alert("Credenciales incorrectas. Intenta con apoderado@jardin.cl y 1234");
      }
    }

    function generarCalendario() {
      const calendar = document.getElementById("calendar");
      calendar.innerHTML = "";
      let asistidos = 0;
      let total = 30; // Junio tiene 30 días

      for (let dia = 1; dia <= total; dia++) {
        const div = document.createElement("div");
        div.classList.add("day");
        if (diasAsistencia[dia] === true) {
          div.classList.add("present");
          asistidos++;
        } else if (diasAsistencia[dia] === false) {
          div.classList.add("absent");
        }
        div.textContent = dia;
        calendar.appendChild(div);
      }

      const porcentaje = Math.round((asistidos / total) * 100);
      document.getElementById("porcentajeAsistencia").textContent = `Asistencia: ${porcentaje}% (${asistidos}/${total} días)`;
    }

    function toggleEditar() {
      const form = document.getElementById("formEditar");
      form.style.display = form.style.display === "flex" ? "none" : "flex";

      if (form.style.display === "flex") {
        document.getElementById("inputNombre").value = document.getElementById("nombreNiña").textContent;
        document.getElementById("inputEdad").value = document.getElementById("edad").textContent;
        document.getElementById("inputGrupo").value = document.getElementById("grupo").textContent;
        document.getElementById("inputAlergias").value = document.getElementById("alergias").textContent;
      }
    }

    function guardarCambios() {
      const nombre = document.getElementById("inputNombre").value;
      const edad = document.getElementById("inputEdad").value;
      const grupo = document.getElementById("inputGrupo").value;
      const alergias = document.getElementById("inputAlergias").value;

      if (nombre) document.getElementById("nombreNiña").textContent = nombre;
      if (edad) document.getElementById("edad").textContent = edad;
      if (grupo) document.getElementById("grupo").textContent = grupo;
      if (alergias) document.getElementById("alergias").textContent = alergias;

      toggleEditar();
    }

    function toggleMapa() {
      const mapa = document.getElementById("mapa");
      const btnMapa = document.getElementById("btnMapa");
      if (mapa.style.display === "block") {
        mapa.style.display = "none";
        btnMapa.textContent = "Mostrar mapa ubicación";
      } else {
        mapa.style.display = "block";
        btnMapa.textContent = "Ocultar mapa ubicación";
      }
    }

    function marcarSalida() {
      if (solicitarPermisoNotificacion()) {
        mostrarNotificacion("Salida Jardín", "Tu hijo salió del jardín.");
      }
      agregarNotificacion("Tu hijo salió del jardín.");
      alert("Se ha marcado la salida del niño.");
    }

    function toggleNotificaciones() {
      const panel = document.getElementById("panelNotificaciones");
      if (panel.style.display === "block") {
        panel.style.display = "none";
      } else {
        panel.style.display = "block";
      }
    }

    // Código QR
    function mostrarQR() {
      const modal = document.getElementById("modalQR");
      const canvas = document.getElementById("canvasQR");
      const nombre = document.getElementById("nombreNiña").textContent;
      const grupo = document.getElementById("grupo").textContent;
      const qrData = `Nombre: ${nombre}\nGrupo: ${grupo}`;
      QRCode.toCanvas(canvas, qrData, { width: 200 }, function (error) {
        if (error) console.error(error);
      });
      modal.style.display = "block";
    }
    function cerrarQR() {
      document.getElementById("modalQR").style.display = "none";
    }
  </script>


</body></html>
