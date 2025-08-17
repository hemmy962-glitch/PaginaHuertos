<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Huerto Inteligente - Sistema Modular de Monitoreo</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
  <style>
    /* Aquí van todos tus estilos CSS, incluyendo mejoras visuales */
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
    .button-primary {
      background: white;
      color: #2e7d32;
      padding: 12px 25px;
      border-radius: 30px;
      font-weight: bold;
      transition: background 0.3s, transform 0.2s;
      display: inline-block;
    }
    .button-primary:hover {
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
      grid-template-columns: repeat(auto-fit,minmax(250px,1fr));
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
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .gallery img {
      width: 100%;
      border-radius: 10px;
      box-shadow: 0 6px 12px rgba(0,0,0,0.15);
      transition: transform 0.3s ease, opacity 0.6s ease;
      opacity: 0;
      transform: scale(0.95);
    }
    .gallery img.visible {
      opacity: 1;
      transform: scale(1);
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
    #topBtn, #langSwitch {
      position: fixed;
      z-index: 999;
      border: none;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }
    #topBtn {
      bottom: 20px;
      right: 20px;
      background: #43a047;
      color: white;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 24px;
      display: none;
    }
    #langSwitch {
      top: 10px;
      right: 10px;
      background: #43a047;
      color: white;
      padding: 8px 15px;
      border-radius: 20px;
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
    <section id="proyecto"><h2>Proyecto</h2><p></p></section>
    <section aria-label="Visión del Proyecto"><h2>Visión</h2><p></p></section>
    <section aria-label="Ventajas del proyecto"><h2>Ventajas</h2><div class="card-container"></div></section>
    <section aria-label="Impacto del proyecto"><h2>Impacto</h2><p></p></section>
    <section aria-label="Equipo"><h2>Equipo</h2><div class="team-container"></div></section>
    <section aria-label="Galería" class="gallery">
      <a href="#"><img src="https://source.unsplash.com/400x300/?garden" alt="Imagen 1" /></a>
      <a href="#"><img src="https://source.unsplash.com/400x300/?plants" alt="Imagen 2" /></a>
      <a href="#"><img src="https://source.unsplash.com/400x300/?agriculture" alt="Imagen 3" /></a>
    </section>
    <div id="lightbox"><img id="lightbox-img" src="" alt="" /></div>
    <section aria-label="Datos de humedad"><h2>Datos del Sensor</h2><p id="sensorData">-- % Humedad</p><canvas id="humidityChart" width="400" height="200"></canvas></section>
    <section aria-label="Preguntas Frecuentes"><h2>FAQ</h2><div id="faq-container"></div></section>
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
        <p id="formMessage" aria-live="polite"></p>
      </form>
    </section>
  </main>
  <footer>
    <div class="social-icons"></div>
    <p>© 2025 Sistema Modular Inteligente para Monitoreo de Humedad en Huertos</p>
  </footer>
  <button id="topBtn" aria-label="Volver arriba">↑</button>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    const langSwitch = document.getElementById('langSwitch');
    const topBtn = document.getElementById('topBtn');
    let lang = 'es';
    const texts = {
      es: {
        title: "Huerto Inteligente - Sistema Modular de Monitoreo",
        headerTitle: "Huerto Inteligente",
        headerSpan: "Sistema Modular de Monitoreo",
        headerSubtitle: "Tecnología para una agricultura más eficiente y sostenible",
        btnPrimary: "Conocer más",
        proyectoTitle: "Proyecto",
        proyectoDesc: "Este sistema inteligente...",
        visionTitle: "Visión",
        visionDesc: "Visualizamos un futuro...",
        ventajasTitle: "Ventajas",
        ventajas: [
          {title:"Modular", desc:"Fácil de escalar...", icon:"https://img.icons8.com/ios/50/modular.png"},
          {title:"Monitoreo Remoto", desc:"Consulta datos...", icon:"https://img.icons8.com/ios/50/remote.png"}
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
        proyectoDesc: "This intelligent, modular, and low-cost system monitors soil moisture in gardens using IoT sensors, local and remote connectivity, and a secure responsive web platform...",
        visionTitle: "Vision",
        visionDesc: "We envision a future where our modular system is widely adopted by small producers and schools...",
        ventajasTitle: "Advantages",
        ventajas: [
          {title:"Modular", desc:"Easy to scale and adapt to different gardens.", icon:"https://img.icons8.com/ios/50/modular.png"},
          {title:"Remote Monitoring", desc:"Check real-time data from anywhere.", icon:"https://img.icons8.com/ios/50/remote.png"}
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
          {q:"What sensors does the system use?", a:"We use soil moisture sensors compatible with ESP32 microcontrollers..."},
          {q:"Is internet connection needed for monitoring?", a:"The system can operate with or without internet connection..."},
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

    function updateTexts() {
      document.title = texts[lang].title;
      document.querySelector('header h1').innerHTML = `${texts[lang].headerTitle} <span>${texts[lang].headerSpan}</span>`;
      document.querySelector('header p').textContent = texts[lang].headerSubtitle;
      document.querySelector('.button-primary').textContent = texts[lang].btnPrimary;
      document.querySelector('#proyecto h2').textContent = texts[lang].proyectoTitle;
      document.querySelector('#proyecto p').textContent = texts[lang].proyectoDesc;
      document.querySelector('section[aria-label="Visión del Proyecto"] h2').textContent = texts[lang].visionTitle;
      document.querySelector('section[aria-label="Visión del Proyecto"] p').textContent = texts[lang].visionDesc;
      document.querySelector('section[aria-label="Ventajas del proyecto"] h2').textContent = texts[lang].ventajasTitle;
      const cards = document.querySelectorAll('.card-container .card');
      cards.forEach((card, i) => {
        const v = texts[lang].ventajas[i];
        card.querySelector('img').src = v.icon;
        card.querySelector('h3').textContent = v.title;
        card.querySelector('p').textContent = v.desc;
      });
      document.querySelector('section[aria-label="Impacto del proyecto"] h2').textContent = texts[lang].impactoTitle;
      document.querySelector('section[aria-label="Impacto del proyecto"] p').textContent = texts[lang].impactoDesc;
      document.querySelector('section[aria-label="Equipo"] h2').textContent = texts[lang].equipoTitle;
      const team = document.querySelectorAll('.team-container .team-member');
      team.forEach((member, i) => {
        member.querySelector('h3').textContent = texts[lang].equipo[i].nombre;
        member.querySelector('p').textContent = texts[lang].equipo[i].rol;
      });
      document.querySelector('section[aria-label="Galería"] h2').textContent = texts[lang].galeriaTitle;
      document.querySelector('section[aria-label="Datos de humedad"] h2').textContent = texts[lang].sensorTitle;
      document.querySelector('section[aria-label="Preguntas Frecuentes"] h2').textContent = texts[lang].faqTitle;
      const faqBtns = document.querySelectorAll('.faq-question');
      faqBtns.forEach((btn, i) => {
        btn.textContent = texts[lang].faqs[i].q;
        const answer = document.getElementById(btn.getAttribute('aria-controls'));
        answer.querySelector('p').textContent = texts[lang].faqs[i].a;
      });
      document.querySelector('section[aria-label="Contacto"] h2').textContent = texts[lang].contactoTitle;
      document.querySelector('label[for="name"]').textContent = texts[lang].contactoLabels.name;
      document.querySelector('label[for="email"]').textContent = texts[lang].contactoLabels.email;
      document.querySelector('label[for="message"]').textContent = texts[lang].contactoLabels.message;
      document.getElementById('name').placeholder = lang === 'es' ? 'Tu nombre' : 'Your name';
      document.getElementById('email').placeholder = lang === 'es' ? 'tu@email.com' : 'your@email.com';
      document.getElementById('message').placeholder = lang === 'es' ? 'Escribe tu mensaje aquí' : 'Write your message here';
      document.querySelector('button[type="submit"]').textContent = texts[lang].contactoBtn;
      document.querySelector('footer p').textContent = texts[lang].footerText;
      langSwitch.textContent = texts[lang].langSwitchBtn;
      topBtn.setAttribute('aria-label', texts[lang].topBtnAria);
    }

    langSwitch.addEventListener('click', () => {
      lang = lang === 'es' ? 'en' : 'es';
      document.documentElement.lang = lang;
      updateTexts();
    });

    window.addEventListener('scroll', () => {
      topBtn.style.display = window.scrollY > 200 ? 'block' : 'none';
    });

    topBtn.addEventListener('click', () => {
      window.scrollTo({top: 0, behavior: 'smooth'});
    });

    document.querySelectorAll('.gallery img').forEach(img => {
      const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) img.classList.add('visible');
        });
      }, { threshold: 0.2 });
      observer.observe(img);
    });

    const lightbox = document.getElementById('lightbox');
    const light
    updateTexts();

    // Sensor + gráfico
    const sensorDataDiv = document.getElementById('sensorData');
    const ctx = document.getElementById('humidityChart')?.getContext('2d');
    let labels = [], dataPoints = [], maxPoints = 12;

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
      document.addEventListener('keydown', e => {
        if (e.key === 'Escape') lightbox.style.display = 'none';
      });
    }

    // EmailJS
    emailjs.init("WvlxNjRXrVa36vEQ4");
    const contactForm = document.getElementById('contactForm');
    const formMessage = document.getElementById('formMessage');

    if(contactForm){
      contactForm.addEventListener('submit', function(e) {
        e.preventDefault();
        formMessage.textContent = texts[lang].contactoSending;
        formMessage.style.color = '#2e7d32';

        emailjs.sendForm('service_mc5m6mt', 'template_x2rqp4l', this)
          .then(() => {
            formMessage.textContent = texts[lang].contactoThanks;
            contactForm.reset();
          }, (error) => {
            formMessage.textContent = texts[lang].contactoError;
            formMessage.style.color = 'red';
            console.error('Error:', error);
          });
      });
    }
  </script>
</body>
</html>
