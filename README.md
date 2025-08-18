
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Huerto Inteligente - Sistema Modular de Monitoreo</title>
<style>
  /* Reset y estilos base */
  *, *::before, *::after {
    box-sizing: border-box;
  }
  body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    background-color: #f4f8f5;
    color: #333;
    scroll-behavior: smooth;
    line-height: 1.6;
  }
  a {
    text-decoration: none;
    color: #2e7d32;
  }
  a:hover, button:hover {
    color: #43a047;
  }
  header, footer {
    background: linear-gradient(to right, #43a047, #2e7d32);
    color: white;
    text-align: center;
    padding: 80px 20px;
  }
  header h1 {
    font-size: 3.5rem;
    margin-bottom: 10px;
    font-weight: 700;
  }
  header h1 span {
    display: block;
    font-size: 1.6rem;
    font-weight: 400;
    margin-top: 5px;
    color: #a5d6a7;
    font-style: italic;
  }
  header a.button-primary {
    background: white;
    color: #2e7d32;
    padding: 12px 25px;
    border-radius: 30px;
    font-weight: bold;
    transition: background 0.3s, transform 0.2s;
    display: inline-block;
  }
  header a.button-primary:hover {
    background: #c8e6c9;
    transform: scale(1.05);
  }
  section {
    padding: 60px 20px;
    max-width: 1100px;
    margin: auto;
  }
  h2 {
    color: #2e7d32;
    text-align: center;
    margin-bottom: 30px;
  }
 .card-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columnas fijas */
  gap: 20px;
}

.card {
  background: white;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
}

.card img {
  width: 50px;
  margin-bottom: 10px;
}

/* Responsive */
@media(max-width: 800px) {
  .card-container {
    grid-template-columns: repeat(2, 1fr); /* 2 columnas en tabletas */
  }
}

@media(max-width: 500px) {
  .card-container {
    grid-template-columns: 1fr; /* 1 columna en móviles */
  }
}


  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
    gap: 15px;
  }
  .gallery img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    cursor: pointer;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .gallery img.visible {
    opacity: 1;
    transform: translateY(0);
  }
  #lightbox {
    position: fixed;
    top:0; left:0;
    width:100%; height:100%;
    background: rgba(0,0,0,0.8);
    display:none;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  #lightbox img {
    max-width: 90%;
    max-height: 80%;
    border-radius: 8px;
  }
  #lightbox:target {
    display: flex;
  }
  #sensorData {
    background: #e8f5e9;
    border: 2px solid #43a047;
    padding: 30px;
    margin: 40px auto;
    max-width: 300px;
    text-align: center;
    border-radius: 15px;
    font-weight: 700;
    font-size: 2rem;
    color: #2e7d32;
  }
  /* Equipo */
  .team-member {
    background: white;
    padding: 20px;
    margin: 10px;
    border-radius: 15px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    text-align: center;
  }
  .team-member h3 {
    margin-top: 10px;
    color: #2e7d32;
  }
  .team-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
  }
  /* Contacto */
  form {
    max-width: 500px;
    margin: auto;
    background: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  }
  form label {
    display: block;
    margin: 15px 0 5px;
  }
  form input, form textarea {
    width: 100%;
    padding: 10px;
    border: 2px solid #43a047;
    border-radius: 8px;
    resize: vertical;
  }
  form button {
    margin-top: 20px;
    background: #43a047;
    color: white;
    border: none;
    padding: 12px 25px;
    font-weight: bold;
    border-radius: 30px;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
  }
  form button:hover {
    background: #2e7d32;
    transform: scale(1.05);
  }
  /* FAQ */
  .faq-container {
    max-width: 700px;
    margin: auto;
  }
  .faq-item {
    background: white;
    margin-bottom: 15px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    overflow: hidden;
  }
  .faq-question {
    padding: 15px 20px;
    cursor: pointer;
    background: #e8f5e9;
    font-weight: 600;
    color: #2e7d32;
    position: relative;
  }
  .faq-question::after {
    content: '+';
    position: absolute;
    right: 20px;
    font-size: 1.5rem;
    transition: transform 0.3s;
  }
  .faq-question.active::after {
    content: '-';
  }
  .faq-answer {
    max-height: 0;
    padding: 0 20px;
    transition: max-height 0.35s ease;
    overflow: hidden;
    background: white;
  }
  .faq-answer p {
    margin: 15px 0;
  }
  /* Redes sociales footer */
  .social-icons {
    display: flex;
    justify-content: center;
    gap: 25px;
    margin-top: 15px;
  }
  .social-icons a {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 45px;
    height: 45px;
    border-radius: 50%;
    background-color: #2e7d32;
    transition: background-color 0.3s, transform 0.3s;
  }
  .social-icons a img {
    width: 24px;
    height: 24px;
    filter: invert(100%) sepia(0%) saturate(0%) hue-rotate(93deg) brightness(103%) contrast(103%);
  }
  .social-icons a:hover {
    background-color: #a5d6a7;
    transform: scale(1.15);
    filter: invert(30%) sepia(40%) saturate(300%) hue-rotate(80deg) brightness(90%) contrast(90%);
  }
  footer p {
    margin-top: 20px;
    font-size: 0.9rem;
    color: #dcedc8;
  }
  /* Botón volver arriba */
  #topBtn {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #43a047;
    color: white;
    border: none;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 24px;
    cursor: pointer;
    display: none;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    z-index: 999;
  }
  /* Idioma */
  #langSwitch {
    position: fixed;
    top: 10px;
    right: 10px;
    background: #43a047;
    color: white;
    border: none;
    padding: 8px 15px;
    border-radius: 20px;
    cursor: pointer;
    font-weight: 600;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    z-index: 999;
    user-select: none;
  }
  /* Microinteracciones */
  button, a.button-primary {
    transition: background-color 0.3s, color 0.3s, transform 0.2s;
  }
  button:hover, a.button-primary:hover {
    transform: scale(1.05);
  }
  /* Responsive */
  @media(max-width: 600px) {
    .team-container {
      flex-direction: column;
      align-items: center;
    }
  }
</style>
</head>
<body>

<button id="langSwitch" aria-label="Cambiar idioma">EN</button>

<header>
  <h1>Huerto Inteligente <span>Sistema Modular de Monitoreo</span></h1>
  <p>Tecnología para una agricultura más eficiente y sostenible</p>
  <a href="#proyecto" class="button-primary">Conocer más</a>
</header>

<main>
  <section id="proyecto" aria-label="Descripción del Proyecto">
    <h2>Proyecto</h2>
    <p>Este sistema inteligente, modular y de bajo costo permite monitorear la humedad del suelo en huertos mediante sensores IoT, conectividad local y remota, y una plataforma web segura y responsiva. Facilita la toma de decisiones para el riego y cuidado de cultivos, optimizando el uso del agua y reduciendo el riesgo por exceso o déficit hídrico.</p>
  </section>

  <section aria-label="Visión del Proyecto">
    <h2>Visión</h2>
    <p>Visualizamos un futuro donde nuestro sistema modular sea ampliamente adoptado por pequeños productores y escuelas, permitiendo una agricultura más inteligente, sostenible y adaptada a las necesidades cambiantes del sector. La flexibilidad para agregar más sensores o módulos hace posible la expansión y mejora continua, garantizando soluciones a medida para distintos cultivos y escenarios.</p>
  </section>

 <section aria-label="Ventajas del proyecto">
  <h2>Ventajas</h2>
  <div class="card-container">
    <div class="card" role="article">
      <img src="https://img.icons8.com/?size=100&id=zzlvMAxv9KKB&format=png&color=000000" alt="Modular" />
      <h3>Modular</h3>
      <p>Fácil de escalar y adaptar a diferentes huertos.</p>
    </div>
    <div class="card" role="article">
      <img src="https://img.icons8.com/?size=100&id=hnc1VnzGkyTd&format=png&color=000000" alt="Monitoreo Remoto" />
      <h3>Monitoreo Remoto</h3>
      <p>Consulta datos en tiempo real desde cualquier lugar.</p>
    </div>
    <div class="card" role="article">
      <img src="https://img.icons8.com/fluency/96/water.png" alt="Ahorro de Agua" />
      <h3>Ahorro de Agua</h3>
      <p>Riego eficiente que cuida el recurso hídrico.</p>
    </div>
    <div class="card" role="article">
      <img src="https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000" alt="Seguridad" />
      <h3>Seguridad</h3>
      <p>Protección con login, cifrado y control de usuarios.</p>
    </div>
    <div class="card" role="article">
      <img src="https://img.icons8.com/?size=100&id=12345&format=png&color=000000" alt="Fácil de usar" />
      <h3>Fácil de usar</h3>
      <p>Interfaz intuitiva y sencilla para todos los usuarios.</p>
    </div>
    <div class="card" role="article">
      <img src="https://img.icons8.com/?size=100&id=67890&format=png&color=000000" alt="Expansible" />
      <h3>Expansible</h3>
      <p>Posibilidad de agregar más módulos y sensores en el futuro.</p>
    </div>
  </div>
</section>


  <section aria-label="Impacto del proyecto">
    <h2>Impacto</h2>
    <p>Este sistema ayuda a pequeños productores, escuelas y jardines a optimizar recursos, reducir costos y fomentar la sostenibilidad agrícola.</p>
  </section>

  <section aria-label="Equipo">
    <h2>Equipo</h2>
    <div class="team-member">
      <h3>Elva Nohemi García Ayala</h3>
      <p>Líder del Proyecto y Documentación</p>
    </div>
    <div class="team-member">
      <h3>Héctor Salvador Navarro Bochas</h3>
      <p>Líder Técnico y Programación</p>
    </div>
    <div class="team-member">
      <h3>Luis Daniel Albañil García</h3>
      <p>Soporte y Pruebas</p>
    </div>
  </section>

  <section aria-label="Galería" class="gallery">
    <h2>Galería</h2>
    <a href="#"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRL226GPDjGiNXkUGUV5Dvcx0xVsXDJMQJFVg&s" alt="Imagen 1" /></a>
    <a href="#"><img src="https://canalsenior.es/wp-content/uploads/2021/05/162446444717020210630-iot-agricultura.jpg" alt="Imagen 2" /></a>
    <a href="#"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKkF1d8ZcKQ6P9dw1-3dKG2dV1OSrzfBjOng&s" alt="Imagen 3" /></a>
    <a href="#"><img src="https://www.tecneu.com/cdn/shop/files/sensor-de-humedad-de-tierra-suelo-200579.jpg?v=1750204517&width=720" alt="Imagen 4" /></a>
    <a href="#"><img src="https://m.media-amazon.com/images/I/31H17HFJZIL._UF350,350_QL80_.jpg" alt="Imagen 5" /></a>
    <a href="#"><img src="https://cdn.portalfruticola.com/2025/04/riegointeligente-1024x683.jpg" alt="Imagen 6" /></a>
    <a href="#"><img src="data:image/jpeg;base64,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" alt="Imagen 7" /></a>
    <a href="#"><img src="https://cdn.visionfruticola.com/2024/07/shutterstock_2439322953-1296x700.webp" alt="Imagen 8" /></a>
    <a href="#"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ_Jro-WbYfkSF5oR4gP4tgZD7TBQZiZzjF3w&s" alt="Imagen 9" /></a>

</section>

  <div id="lightbox" role="dialog" aria-modal="true" aria-label="Imagen ampliada">
    <img id="lightbox-img" src="" alt="" />
  </div>

  <section aria-label="Datos de humedad">
    <h2>Datos del Sensor</h2>
    <p id="sensorData">-- % Humedad</p>
    <canvas id="humidityChart" width="400" height="200"></canvas>
  </section>

  <section aria-label="Preguntas Frecuentes">
    <h2>FAQ</h2>

    <div class="faq-item">
      <button class="faq-question" aria-expanded="false" aria-controls="faq1">¿Qué sensores utiliza el sistema?</button>
      <div id="faq1" class="faq-answer" hidden><p>Usamos sensores de humedad del suelo compatibles con microcontroladores ESP32 para garantizar precisión y bajo consumo.</p></div>
    </div>

    <div class="faq-item">
      <button class="faq-question" aria-expanded="false" aria-controls="faq2">¿Se necesita conexión a internet para monitorear?</button>
      <div id="faq2" class="faq-answer" hidden><p>El sistema puede funcionar con o sin conexión a internet gracias a su comunicación local y almacenamiento en servidor local.</p></div>
    </div>

    <div class="faq-item">
      <button class="faq-question" aria-expanded="false" aria-controls="faq3">¿Quién puede usar este sistema?</button>
      <div id="faq3" class="faq-answer" hidden><p>Está diseñado para pequeños productores, huertos escolares, jardines y desarrolladores interesados en agricultura inteligente.</p></div>
    </div>
  </section>

  <section aria-label="Contacto">
    <h2>Contacto</h2>
    <form id="contactForm" novalidate>
      <label for="name">Nombre:</label>
      <input type="text" id="name" name="name" required placeholder="Tu nombre" />
      
      <label for="email">Correo electrónico:</label>
      <input type="email" id="email" name="email" required placeholder="tu@email.com" />
      
      <label for="message">Mensaje:</label>
      <textarea id="message" name="message" rows="4" required placeholder="Escribe tu mensaje aquí"></textarea>
      
      <button type="submit">Enviar</button>
      <p id="formMessage" aria-live="polite" style="margin-top: 10px; font-weight: 600;"></p>
    </form>
  </section>
</main>

<footer>
  <div class="social-icons">
    <a href="https://www.facebook.com/share/176EKaone8/?mibextid=wwXIfr" target="_blank" aria-label="Facebook" rel="noopener noreferrer">
      <img src="https://img.icons8.com/?size=100&id=62225&format=png&color=000000" alt="Facebook" />
    </a>
    <a href="https://youtube.com/@hemmy-2304?si=6qmBqV8vIRfugojz" target="_blank" aria-label="YouTube" rel="noopener noreferrer">
      <img src="https://img.icons8.com/?size=120&id=37325&format=png&color=000000" alt="YouTube" />
    </a>
    <a href="https://www.tiktok.com/@hemmy_19?is_from_webapp=1&sender_device=pc" target="_blank" aria-label="TikTok" rel="noopener noreferrer">
      <img src="https://img.icons8.com/?size=100&id=jWD8DpTON7FB&format=png&color=000000" alt="TikTok" />
    </a>
  </div>
  <p>© 2025 Sistema Modular Inteligente para Monitoreo de Humedad en Huertos</p>
</footer>


<button id="topBtn" aria-label="Volver arriba">↑</button>

<!-- Librerías -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.emailjs.com/dist/email.min.js"></script>

<script>
  // Variables globales
  const topBtn = document.getElementById('topBtn');
  const langSwitch = document.getElementById('langSwitch');
  let lang = 'es';

  // Textos para idiomas
  const texts = {
    es: {
      title: "Huerto Inteligente - Sistema Modular de Monitoreo",
      headerTitle: "Huerto Inteligente",
      headerSpan: "Sistema Modular de Monitoreo",
      headerSubtitle: "Tecnología para una agricultura más eficiente y sostenible",
      btnPrimary: "Conocer más",
      proyectoTitle: "Proyecto",
      proyectoDesc: "Este sistema inteligente, modular y de bajo costo permite monitorear la humedad del suelo en huertos mediante sensores IoT, conectividad local y remota, y una plataforma web segura y responsiva. Facilita la toma de decisiones para el riego y cuidado de cultivos, optimizando el uso del agua y reduciendo el riesgo por exceso o déficit hídrico.",
      visionTitle: "Visión",
      visionDesc: "Visualizamos un futuro donde nuestro sistema modular sea ampliamente adoptado por pequeños productores y escuelas, permitiendo una agricultura más inteligente, sostenible y adaptada a las necesidades cambiantes del sector. La flexibilidad para agregar más sensores o módulos hace posible la expansión y mejora continua, garantizando soluciones a medida para distintos cultivos y escenarios.",
     ventajasTitle: "Ventajas",
ventajas: [
  {icon:"https://img.icons8.com/?size=100&id=zzlvMAxv9KKB&format=png&color=000000", title:"Modular", desc:"Fácil de escalar y adaptar a diferentes huertos."},
  {icon:"https://img.icons8.com/?size=100&id=hnc1VnzGkyTd&format=png&color=000000", title:"Monitoreo Remoto", desc:"Consulta datos en tiempo real desde cualquier lugar."},
  {icon:"https://img.icons8.com/fluency/96/water.png", title:"Ahorro de Agua", desc:"Riego eficiente que cuida el recurso hídrico."},
  {icon:"https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000", title:"Seguridad", desc:"Protección con login, cifrado y control de usuarios."},
  {icon:"https://img.icons8.com/?size=100&id=79056&format=png&color=000000", title:"Alertas Inteligentes", desc:"Recibe notificaciones cuando la humedad es baja o hay condiciones críticas en el huerto."},
  {icon:"https://img.icons8.com/?size=100&id=97612&format=png&color=000000", title:"Fomenta la Comunidad", desc:"Ideal para huertos escolares o urbanos, promoviendo colaboración y aprendizaje."}
],
      impactoTitle: "Impacto",
      impactoDesc: "Este sistema ayuda a pequeños productores, escuelas y jardines a optimizar recursos, reducir costos y fomentar la sostenibilidad agrícola.",
      equipoTitle: "Equipo",
      equipo: [
        {nombre:"Elva Nohemi García Ayala", rol:"Líder del Proyecto y Documentación"},
        {nombre:"Héctor Salvador Navarro Bochas", rol:"Líder Técnico y Programación"},
        {nombre:"Luis Daniel Albañil García", rol:"Soporte y Pruebas"}
      ],
      galeriaTitle: "Galería",
      sensorTitle: "Datos del Sensor",
      faqTitle: "Preguntas Frecuentes",
      faqs: [
        {q:"¿Qué sensores utiliza el sistema?", a:"Usamos sensores de humedad del suelo compatibles con microcontroladores ESP32 para garantizar precisión y bajo consumo."},
        {q:"¿Se necesita conexión a internet para monitorear?", a:"El sistema puede funcionar con o sin conexión a internet gracias a su comunicación local y almacenamiento en servidor local."},
        {q:"¿Quién puede usar este sistema?", a:"Está diseñado para pequeños productores, huertos escolares, jardines y desarrolladores interesados en agricultura inteligente."}
      ],
      contactoTitle: "Contacto",
      contactoLabels: {name:"Nombre:", email:"Correo electrónico:", message:"Mensaje:"},
      contactoBtn: "Enviar",
      contactoSending: "Enviando mensaje...",
      contactoThanks: "¡Gracias por contactarnos! Responderemos pronto.",
      contactoError: "Error al enviar el mensaje. Intenta nuevamente.",
      footerText: "© 2025 Huerto Inteligente. Todos los derechos reservados.",
      langSwitchBtn: "EN",
      topBtnAria: "Volver arriba"
    },
    en: {
      title: "Smart Garden - Modular Monitoring System",
      headerTitle: "Smart Garden",
      headerSpan: "Modular Monitoring System",
      headerSubtitle: "Technology for more efficient and sustainable agriculture",
      btnPrimary: "Learn more",
      proyectoTitle: "Project",
      proyectoDesc: "This intelligent, modular, and low-cost system monitors soil moisture in gardens using IoT sensors, local and remote connectivity, and a secure responsive web platform. It facilitates decision making for irrigation and crop care, optimizing water use and reducing risks from excess or deficient moisture.",
      visionTitle: "Vision",
      visionDesc: "We envision a future where our modular system is widely adopted by small producers and schools, enabling smarter, sustainable agriculture adapted to the changing needs of the sector. The flexibility to add more sensors or modules allows expansion and continuous improvement, providing tailored solutions for different crops and scenarios.",
ventajasTitle: "Advantages",
ventajas: [
  {icon:"https://img.icons8.com/?size=100&id=zzlvMAxv9KKB&format=png&color=000000", title:"Modular", desc:"Easy to scale and adapt to different gardens."},
  {icon:"https://img.icons8.com/?size=100&id=hnc1VnzGkyTd&format=png&color=000000", title:"Remote Monitoring", desc:"Check real-time data from anywhere."},
  {icon:"https://img.icons8.com/fluency/96/water.png", title:"Water Saving", desc:"Efficient irrigation that protects water resources."},
  {icon:"https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000", title:"Security", desc:"Protection with login, encryption, and user control."},
  {icon:"https://img.icons8.com/?size=100&id=79056&format=png&color=000000", title:"Smart Alerts", desc:"Receive notifications when soil moisture is low or conditions are critical."},
  {icon:"https://img.icons8.com/?size=100&id=97612&format=png&color=000000", title:"Community Focus", desc:"Ideal for school or urban gardens, promoting collaboration and learning."}
],
      impactoTitle: "Impact",
      impactoDesc: "This system helps small producers, schools, and gardens optimize resources, reduce costs, and promote sustainable agriculture.",
      equipoTitle: "Team",
      equipo: [
        {nombre:"Elva Nohemi García Ayala", rol:"Project Leader and Documentation"},
        {nombre:"Héctor Salvador Navarro Bochas", rol:"Technical Leader and Programming"},
        {nombre:"Luis Daniel Albañil García", rol:"Support and Testing"}
      ],
      galeriaTitle: "Gallery",
      sensorTitle: "Sensor Data",
      faqTitle: "Frequently Asked Questions",
      faqs: [
        {q:"What sensors does the system use?", a:"We use soil moisture sensors compatible with ESP32 microcontrollers to ensure accuracy and low power consumption."},
        {q:"Is internet connection needed for monitoring?", a:"The system can operate with or without internet connection thanks to local communication and local server storage."},
        {q:"Who can use this system?", a:"It is designed for small producers, school gardens, and developers interested in smart agriculture."}
      ],
      contactoTitle: "Contact",
      contactoLabels: {name:"Name:", email:"Email:", message:"Message:"},
      contactoBtn: "Send",
      contactoSending: "Sending message...",
      contactoThanks: "Thank you for contacting us! We will respond soon.",
      contactoError: "Error sending message. Please try again.",
      footerText: "© 2025 Smart Garden. All rights reserved.",
      langSwitchBtn: "ES",
      topBtnAria: "Back to top"
    }
  };

  // Actualizar textos dinámicamente
  function updateTexts() {
    document.title = texts[lang].title;

    // Header
    const headerH1 = document.querySelector('header h1');
    if(headerH1) headerH1.innerHTML = `${texts[lang].headerTitle} <span>${texts[lang].headerSpan}</span>`;

    const headerP = document.querySelector('header p');
    if(headerP) headerP.textContent = texts[lang].headerSubtitle;

    const btnPrimary = document.querySelector('header a.button-primary');
    if(btnPrimary) btnPrimary.textContent = texts[lang].btnPrimary;

    // Secciones principales
    const proyectoSection = document.querySelector('#proyecto');
    if(proyectoSection){
      proyectoSection.querySelector('h2').textContent = texts[lang].proyectoTitle;
      proyectoSection.querySelector('p').textContent = texts[lang].proyectoDesc;
    }

    const visionSection = document.querySelector('section[aria-label="Visión del Proyecto"], section[aria-label="Vision"]');
    if(visionSection){
      visionSection.querySelector('h2').textContent = texts[lang].visionTitle;
      visionSection.querySelector('p').textContent = texts[lang].visionDesc;
    }

    // Ventajas
    const ventajasSection = document.querySelector('section[aria-label="Ventajas del proyecto"], section[aria-label="Advantages"]');
    if(ventajasSection){
      ventajasSection.querySelector('h2').textContent = texts[lang].ventajasTitle;
      const cards = ventajasSection.querySelectorAll('.card');
      texts[lang].ventajas.forEach((v,i) => {
        if(cards[i]){
          cards[i].querySelector('img').src = v.icon;
          cards[i].querySelector('h3').textContent = v.title;
          cards[i].querySelector('p').textContent = v.desc;
        }
      });
    }

    // Impacto
    const impactoSection = document.querySelector('section[aria-label="Impacto del proyecto"], section[aria-label="Impact"]');
    if(impactoSection){
      impactoSection.querySelector('h2').textContent = texts[lang].impactoTitle;
      impactoSection.querySelector('p').textContent = texts[lang].impactoDesc;
    }

    // Equipo
    const equipoSection = document.querySelector('section[aria-label="Equipo"], section[aria-label="Team"]');
    if(equipoSection){
      equipoSection.querySelector('h2').textContent = texts[lang].equipoTitle;
      const members = equipoSection.querySelectorAll('.team-member');
      texts[lang].equipo.forEach((m,i) => {
        if(members[i]){
          members[i].querySelector('h3').textContent = m.nombre;
          members[i].querySelector('p').textContent = m.rol;
        }
      });
    }

    // Galería
    const galeriaSection = document.querySelector('section[aria-label="Galería"], section[aria-label="Gallery"]');
    if(galeriaSection){
      galeriaSection.querySelector('h2').textContent = texts[lang].galeriaTitle;
    }

    // Sensor
    const sensorSection = document.querySelector('section[aria-label="Datos de humedad"], section[aria-label="Sensor Data"]');
    if(sensorSection){
      sensorSection.querySelector('h2').textContent = texts[lang].sensorTitle;
    }

    // FAQ
    const faqSection = document.querySelector('section[aria-label="Preguntas Frecuentes"], section[aria-label="Frequently Asked Questions"]');
    if(faqSection){
      faqSection.querySelector('h2').textContent = texts[lang].faqTitle;
      const faqBtns = faqSection.querySelectorAll('.faq-question');
      texts[lang].faqs.forEach((faq,i) => {
        if(faqBtns[i]){
          faqBtns[i].textContent = faq.q;
          const answer = document.getElementById(faqBtns[i].getAttribute('aria-controls'));
          if(answer) answer.querySelector('p').textContent = faq.a;
        }
      });
    }

    // Contacto
    const contactoSection = document.querySelector('section[aria-label="Contacto"], section[aria-label="Contact"]');
    if(contactoSection){
      contactoSection.querySelector('h2').textContent = texts[lang].contactoTitle;
      contactoSection.querySelector('label[for="name"]').textContent = texts[lang].contactoLabels.name;
      contactoSection.querySelector('label[for="email"]').textContent = texts[lang].contactoLabels.email;
      contactoSection.querySelector('label[for="message"]').textContent = texts[lang].contactoLabels.message;
      contactoSection.querySelector('button[type="submit"]').textContent = texts[lang].contactoBtn;
    }

    // Footer
    const footerP = document.querySelector('footer p');
    if(footerP) footerP.textContent = texts[lang].footerText;

    // Botones y aria-labels
    if(langSwitch) langSwitch.textContent = texts[lang].langSwitchBtn;
    if(topBtn) topBtn.setAttribute('aria-label', texts[lang].topBtnAria);
  }

  // Cambiar idioma
  if(langSwitch){
    langSwitch.addEventListener('click', () => {
      lang = lang === 'es' ? 'en' : 'es';
      document.documentElement.lang = lang;
      updateTexts();
    });
  }

  // Botón volver arriba
  window.addEventListener('scroll', () => {
    if(topBtn){
      topBtn.style.display = window.scrollY > 200 ? 'block' : 'none';
    }
  });
  if(topBtn){
    topBtn.addEventListener('click', () => {
      window.scrollTo({top: 0, behavior: 'smooth'});
    });
  }

  // Animación galería al scroll
  const images = document.querySelectorAll('.gallery img');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.2 });
  images.forEach(img => observer.observe(img));

  // Lightbox
  const lightbox = document.getElementById('lightbox');
  const lightboxImg = document.getElementById('lightbox-img');
  document.querySelectorAll('.gallery a').forEach(link => {
    link.addEventListener('click', e => {
      e.preventDefault();
      if(lightbox && lightboxImg){
        lightbox.style.display = 'flex';
        lightboxImg.src = link.querySelector('img').src;
        lightboxImg.alt = link.querySelector('img').alt;
      }
    });
  });
  if(lightbox){
    lightbox.addEventListener('click', () => {
      lightbox.style.display = 'none';
    });
  }

  // Simulación datos sensor + gráfico
  const sensorDataDiv = document.getElementById('sensorData');
  const ctx = document.getElementById('humidityChart')?.getContext('2d');

  let labels = [];
  let dataPoints = [];
  const maxPoints = 12;

  const humidityChart = ctx ? new Chart(ctx, {
    type: 'line',
    data: {
      labels: labels,
      datasets: [{
        label: lang === 'es' ? 'Humedad (%)' : 'Humidity (%)',
        data: dataPoints,
        borderColor: '#43a047',
        backgroundColor: 'rgba(67, 160, 71, 0.2)',
        tension: 0.3,
        fill: true,
        pointRadius: 4,
        pointHoverRadius: 7,
      }]
    },
    options: {
      responsive: true,
      scales: {
        y: { min: 0, max: 100, ticks: { stepSize: 10 } }
      },
      plugins: {
        legend: { display: true, labels: {color: '#2e7d32'} }
      }
    }
  }) : null;

  function getRandomHumidity() {
    return (30 + Math.random() * 40).toFixed(1);
  }

  function updateSensorData() {
    const humidity = getRandomHumidity();
    const now = new Date();
    const timeLabel = now.toLocaleTimeString();

    if(sensorDataDiv) sensorDataDiv.textContent = humidity + (lang === 'es' ? ' % Humedad' : ' % Humidity');

    if(labels.length >= maxPoints) {
      labels.shift();
      dataPoints.shift();
    }
    labels.push(timeLabel);
    dataPoints.push(humidity);

    if(humidityChart) {
      humidityChart.data.labels = labels;
      humidityChart.data.datasets[0].label = lang === 'es' ? 'Humedad (%)' : 'Humidity (%)';
      humidityChart.data.datasets[0].data = dataPoints;
      humidityChart.update();
    }
  }

  updateTexts();
  updateSensorData();
  setInterval(updateSensorData, 5000);

  // FAQ toggle
  document.querySelectorAll('.faq-question').forEach(btn => {
    btn.addEventListener('click', () => {
      const expanded = btn.getAttribute('aria-expanded') === 'true';
      btn.setAttribute('aria-expanded', !expanded);
      const answer = document.getElementById(btn.getAttribute('aria-controls'));
      if (!expanded) {
        answer.hidden = false;
        answer.style.maxHeight = answer.scrollHeight + 'px';
        btn.classList.add('active');
      } else {
        answer.style.maxHeight = null;
        setTimeout(() => { answer.hidden = true; }, 350);
        btn.classList.remove('active');
      }
    });
  });

  // EmailJS init
  emailjs.init("WvlxNjRXrVa36vEQ4");

  // Enviar formulario contacto
  const contactForm = document.getElementById('contactForm');
  const formMessage = document.getElementById('formMessage');

  if(contactForm){
    contactForm.addEventListener('submit', function(e) {
      e.preventDefault();
      formMessage.textContent = texts[lang].contactoSending;

      emailjs.sendForm('service_mc5m6mt', 'template_x2rqp4l', this)
        .then(() => {
          formMessage.textContent = texts[lang].contactoThanks;
          contactForm.reset();
        }, (error) => {
          formMessage.textContent = texts[lang].contactoError;
          console.error('Error:', error);
        });
    });
  }
</script>

</body>
</html>
