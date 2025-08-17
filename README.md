
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
  <a class="button-primary">Conocer más</a>
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
        <img src="https://img.icons8.com/?size=100&id=zzlvMAxv9KKB&format=png&color=000000" alt="Icono Modular" />
        <h3>Modular</h3>
        <p>Fácil de escalar y adaptar a diferentes huertos.</p>
      </div>
      <div class="card" role="article">
        <img src="https://img.icons8.com/?size=100&id=hnc1VnzGkyTd&format=png&color=000000" alt="Icono Monitoreo Remoto" />
        <h3>Monitoreo Remoto</h3>
        <p>Consulta datos en tiempo real desde cualquier lugar.</p>
      </div>
      <div class="card" role="article">
        <img src="https://img.icons8.com/fluency/96/water.png" alt="Icono Ahorro de Agua" />
        <h3>Ahorro de Agua</h3>
        <p>Riego eficiente que cuida el recurso hídrico.</p>
      </div>
      <div class="card" role="article">
        <img src="https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000" alt="Icono Seguridad" />
        <h3>Seguridad</h3>
        <p>Protección con login, cifrado y control de usuarios.</p>
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
       <h2>Galería</h2>
    <a href="#"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRDJX_pk116vnAv8V04KAein3ePKEe6_can7Q&s" alt="Imagen 1" /></a>
    <a href="#"><img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxQTEhUTExMVFhUXGBkaGBgXGBgaHRobGBcXGBgeGBcYHSggGxolHRgYITEhJSkrLi4uFx8zODMtNygtLisBCgoKDg0OGxAQGy8lICUtLS0tNS0tLS8tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIAKIBNwMBIgACEQEDEQH/xAAbAAACAgMBAAAAAAAAAAAAAAAEBQMGAAECB//EAEEQAAIBAwMCAwYDBgQFBAMBAAECEQADIQQSMQVBIlFhBhMycYGRQqGxFCNSwdHwM2Jy4QeCkrLxFSRD0jRTs6L/xAAZAQADAQEBAAAAAAAAAAAAAAABAgMEAAX/xAAuEQACAgICAgAEBQMFAAAAAAAAAQIRAyESMQRBEyIyUWFxgZGxFELBI0Oh0eH/2gAMAwEAAhEDEQA/ALrp1xUjCs0g5qRxUbscGu2yOK5Spia6tAUWccVutHmt3FrgHcVzcxWveVpmmgzjTmRXJ4rb8Vi1zAR7a4uCpm4qMetdZxAASYFTJYYEyKm1joFGwgNQlnUnd4mJPlU5ZEmCyUGuXpnb06uJHcUq1gK8duaMsiirZx0xrAOflU3u5UGuSBXfFh9w2CqJrtUqdLdEDTmm5R+41gi2+aDL7SZFM3BHahH0ZMmubXRyewb34PaugoapTpzERUmm058qm5pewtoFdV4mjuiWn3s1tQ20dyQM+oBzUv8A6UJXcH2k52gE+fJIAHqaJb2v6fp7n7K99LDqAdlwFfiEglyNpJH+aaCmpaRyfsJ33Jl7amYkKwIHmPEBXT6ZTPgEn/KD8hgECmOk1dq8u61cS4p4a24YfdTXT6ceU0nEryEF9NrArjEMsAhhnlT2phY1zXMK5GMggEfSCDRzaYHH+4+xqBulLO4eE/5fD91yCfWKHGS6DafZ1buOQQzqqjuoIP3PAqn9QQi64PIdv1NW59G5DAOciPEFIyO4EEj61Xutb/enesMABI4IHDD0P+1WxOnsnOgD3dQakUYbZwa4fTFu1P8AEivZOwJDmirDrGa2nT2J8o862NARmRQ+LD2wWDXUk4FRxmmaWxxOa3c0q8mpvy8aOsA21ld+/XdHFZVIZoyVoNjDp2tRiwByMkGi1vb+Jjzil+ntIbnl6j9KJu6jaxG7EcRWP+ocPqoDkyZ0rEXFA6i/uZSAZHlwfSiLGpJViyqoHABn+zTx8uMosHIluWs1N7o7cikmq6m1tQsjxNgsYjvz+VA6f2juoxLKoTvDyIHl60q8v7o7mWO3pyT6VG5IJBU+hrnpevDmVMq0x2I/rQftD1R9P4lX3g8p+H1oZMsmlJHXYyG04zXQtCMNmkXTuu27twNJBIgz2MeQqfV3AGBS6oJIkHgzzFTXkT+51hOs1qWGl5M9wCY+1de+VlO3luKrHtP1X9mcKmd6nBz9h9an9n+sG4UUEQI3T2jsKdTySXL0w0+xl0/2UXeLu8yG3QSaanTpbZmYTu4rnXdft2nVHIXfjd2ntSvrXtDatQH+LtHl50nKar/AEOLLKslZzQ+suAZ5mudD1C3ctW3locSOD3I7fKtavS3GU+7YNmQvc+XOKnPM3aAc/tEjw8DkedQ3OpBQ3hP1/rQmlvAKRcKqZODgz6g0p1OuYFrZQup42mhFS0CnVj7R6tTkHntU2gvu7kAxHn3qp9M63EWzbzMeHJq7dF6ZbezLh1aTMkgjOMdqZ4nF8WdRK+pIy0ADmodZqlcTbYR3ihuq9LTY8XLu1gFECSCcSD3oOxaS1a92VLoJDEiG+eKVyitNh1QbpdYHB2sDtpbqNfctvuhgnmeDQKeyksf2fUOAedw7dhjM/OmfUukM1jZcvkKD8UZ/5hTOC1sGiZPaVri7VIn1MVSPaj2YGs1BvnUBCVUEbN3wiJ3bx/YpXrerKtzapcWlJh1+InjcR8vyOKN0fUrMwGMngkeGfPaM17PjeJjgrfYHJ+jLHsOLcNbvDcOG2lTPowJIpgdb1fTD91qmuBezEXp9P3o3n6Go7nVWtkHDL5jNM2beg5CnOQRNaX48GFZZEWj/AOK2uRT73TWbhH8O+2frls/Sn3T/APi7ZkDU6e7Zn8SEXVHzgK32U1T2UFylzxA4DrzHqe8fl50bc6JaIDciInmsWbG8ffRpx8ZrXZ6foPa/RXv8PVWCf4d4DfVGhh9qI1ms09xZZ0leCCGie2M58q8z0fspYblQatHTOgJYtsEAC4J+n+xNZnJ1URp46i2d37o5BBB7f0rN5AAJgHI86WW9OwuNaZoHIJHnxnuKB6n1FkuJbJBicdyK8+OOUpNJGRKy2m8mydwDDzpTd6khG6Kr2v1q3RCTI55oFbFxgQCyirQwuStj0WPqHUbYAkweaDvddZlKosxSXqz7ds+Ix3ppodoAY9xmtH9JFJSk9CRkrozSWblwgsYrdOFthgCDWVaMcVDtIA6H1u1vbfdsg5Hu2In7zzWr3UVZmYFdoOI+decuhEyTzzUDW2JUAsSTECTJPAAHNRfh2qsCo9RHUSF3Wv3ggzH6ChbPtAgLG5ajEgbgJbyI8/Wq97L6S4uVJg/xSAODz2EGk/urlzUFApe4XIhAWJPeAO2J+VLi8aKm0/QaH2s9okuhhdslP4NjbuPOar2l1kNHi28nvViu+y+qdVUWGXPxPCgA+cme3ESMVWbs2rhV18SEq0EEGOYI5+dWeHFb2Ci26Xq4s2t1oe8yQQcEY5oUe0ha263bTbTiA32yaV9D1lo6hffo3umDKdp4JEKx+X9D2gnD2U1L3/ctu9zM++A8BTmQeC3aPP0zSPDi+l/mddCIuyNKuR9aLvahXgM5lYgya9Cb2O0Yt7TZOeH3NunzBJ9eODjGKr1z2U0qk/8Aud23lMbh/wBJzn0FPDJjk6X8HWVbrXUhcZds7wILE+XkKeexFqXtkzmT+dM/Z2/ptPcZfd70eN29ATiYgkT344q02tHpGUGyqLOVCeEA5xtGQcHAFdLKoSUWtf8AA1aPOuodVuNfeyyC7+9ZUB5y0KB+VXzofs/btmNSlu452xgkIROAWORPeBxWxoLKsGCgMDJaOCIOD5ieZo/T6y5duFSim3E7/CBOZDKeeOwj1rPmy8o/I9CpkGv1T2nbwKLQ5lpn5IBM9sUbpeoWiPCtzgfSRIz3oe6tvC8jDCTJiIAU8geQ88Uy6XoStogMxU+IOYnM9vIA1ghCLdN7DVAS9P02832s7rmAWcb+O4DYU/L0pZrtC1xy42WFiIQTP+ZuADHkPqasWms7193vmOezMOxyf7io7Xs64beL8mfhK+EenMjyJpuVfS/3/wABq1opWl6Sunu+88TlT8UGPFIk/n9qd6TWXGNxQEwsnJUkDyAwTMeXNOr14rcNpraqSBCpu8Wf4okiTnuPrSvWapVUbLZL91A7/wAJJyTIq2TlLek+vzA0J9V7QXJ90UIIPjB8u0EHGf0qxad2CC3FtlYSHDbongmOORVS1vXL1q5cDWA7hXdxkEIoiSJhT8IKxyTTnpWbRLMgmTC9h8v7FHJiliav3+otB/TXucW2XaOcRPqJMgUr9t+ti3YdVO64xgbTgA/ESf4okR2mh9Z1W0j7AyhuI3gGCDyJqsdd1Afw5P5cVt8HxVOPxJ+ukK9aKbeuyTGP5GoV1RQ+Yo3U6POfuP8Aahjp243BvQ16dM4Pt6226/Ft7kGc/Wiun9cKNgj50hfQzwCprlbbjBWfkKPJnUemJZa/ZFxgVDGFuKVEnMyMkjByfI1I1p9NaRbhlXlkOMjAPHBHcdpqh9O1l1QE3XNoO4LuYANxIHAPrT3Ua64+2QWGeBkTA4HPA+3pSZ7ljZTC1GaLjotWVAbkUz1nXguncg5wAPmwH6TVY6D1BSsGo/aJtoWBy304NefjXzpGrM6xv8iyarqGmu6M3NQbisrBbTWnKXN5BMKw5HchpXvHFIdEltmVpL3FG0ux5/1HjdnnjgVTOq6t2cICTsHhHkWALH54X/pFT9P1KqYclm9DAA7Z/kBWuUU3YnjQXwkpHoDuOGQKQc4+1a1d+YKH6UBoOrpAUmR5GZHyJo7R6ckyjK6kz6j5jzrBnhNe9CZsMo77QBr+nK7hmJGKM0ulhRGZo7XgN4CIxW3baBAwBWWc3J0mZvZpSREmspR1PXEED86yqQ8ZtXY6hZWvZnoraoOWuhNrDwgAsR3OTgU/tewizP7TcwQRCoCM/I+lWjpmgtpcO22o+lEa+2EzIA9TEfU0/kfHi+UXoZpkdjQlz+9Kk5PhBUEz/qJ/Pt9KiOgS3fW8ltfeoIDGQdp5A7DGJjufM1AvVwCF3CcRieaOZrhgMpAOcwIHp/SsUckq0TsP1er3QVzjI+f+xNKdR0vTbiRYVS8hmjDSc7hPxEk5j68Vw2rFpgrzBE7vl5T5UXrbSkA4cEblOCCMcelPH4jt9HWD2ulaVIPukX8x+dFe/UCEKxiFxj1Hl9PKhddqbVlghIL9uSQD5kmP51u2gzcUfXy+n1iqSlkceMmHkFrJySfuaW60pppdEBdyJXz5z6cfX50wtsNu8cZB8xHoeRSjq9m3v3AoP4ikMTOJYJPAnJ9Kn4yyRyat/h9wSdLs6HtMXBtm0VnjYAT/AMoMg/ajWa2VBEgnBBUAyRPi2iMwT2z+SB9OVBdG3JkB7ZMGMMpI/MHOPnXej0WyL0lNrq0AzIIa2QwIiZcd/PjBrXn/AKdpONxl7W6v9xI/EupdFg06mCSruTAAEmInuTA5+ZxTDS6fGUx3g+XPy+9LXvKA6XNYAoB5AQ2wQpUbxxgE+KZnERQPRtZqbK7blwXAshm2kFkwEYzIn4jIkGBnvWdrRVKtlmuBVlNrbWBO+eDzwefOgP8A1NAoWYhZIkiQJELjJO0gfLtW9Z0c3rbIzmHMjO2IIIgj5c/Wkd4m1ZcXwwUBgty4ckyO43MN0Y7+g4qfwZd/wP2ix3r52qwJ3HlhntOD5eVRft7TuuuAsR5bSODPH3oX2F6zprlu6Gtsz2h7zxLuYoefdgxKjA4H8y46V7Z6a7dNq3aZXglQ6om4jkAqTBHkauvAeSm3X6Hb9Ar9Xkb1Nq4hxCt4jAG70YeYP04pX7TWEtWTfte8uNcICIsEbiQW/Cdo27viJ7+VR3TYuM1xry6cNu/dEH93eBl9rgAGNs47E8CmWn6fvtvbF+3+8UjdbbKzwyhhypgj7VoxwcaUvTL8Lhvso1m4TZ1qCAPc3JbJLXCBvJYn+LdHzrfsS9w23XbdYCXmQAQI8KbsEk/nRa9IuaSzqLN0eJbDZ7MMDcp7gx/WqdoOsPbZhL+6ION2RK7TB7Hj6VXyFy0TwpNtMm6v1u491x4goJADBQQBiGic+dC6bUbzBmeAcn7xU2m0d1/gsmP4j/vTPSezV8EMzAAGeDOM02OcsfROrFZtjsw+jD9Aaiewvcj/AJoH5mKc9T6YNxkfek+r6f8AwjtV15afoo/H/EHvXdKozcWfJCSf/wDNLb/WrA+Bb/zJtj9QxobXdLdTgUJY0p3Z4qnxr6JPG0MrfVV/gu/dP/pTTp/XLS/Gl+OZ8HbEKZH6d6BtoIkDip9dYGw44z+f+/5UPisZY0MU61aF03C4hh8KSxEAADzJxyeTNTN159QwwFRAAAeT5lj58Y7etU3ZHFNentttse+T9h/WkjBcuQ2dv4fE5v6xizbTgknH5VLpEAyxzQtuBUN7UH7/AKUSy+VFitaxV9T5Uw6b1m4jblO2O0du/wA/rNVHTXsGm3T7kzNBoqp3o9OGuF5AwgNwT9AfPuCD9aXvq2KuvdRyO9J/Zpg6vadsCCIPYEwPTn9PKm+k0wUOAcHua854oxyNPozTxJMqelvuXbcSY4/Ot04XpADHxc1lWjkjQjL5pP8AEMVLrLG4gMBB86UarqwCbk+IYkVmn6o11gmWbsOJgSaV5kkrQthF/RW7J3Iw/wBM5EAnwnn6Uv0vtP7zw3IB7EjB+/B9KSav2v0yEkyzCcIpxHaWgVI3WNPeOwgKroGtsTEjO4gx4dhBBEyIPHfJkTq1FpCuN7LAfGQG7GQdxUj/AJlIPGD51KNPki20DkL2Dd9p/hPl50l0JuLjcbigCCYkT5kciCpBzyaNtdQVAbkMIjeCeOJkzECefQ1lUpp12DixSthRcc3nfdJJJT9M030+oT4VLEEDkxM/5RU3tKts299ple7Eqs8gkFpJwBGZMUpZFRAwZnmS3hgTJkp4VJSeIXymrvkloHHVje3rGHgtjAOTBkmk/XegvdCm7u90DBPvChXyhAjK45/CCPOAAHKXQiJAXIlt0iPTByY70c97SrbZrpCrtyHIODgQp5zgYzVcMZKQ0HTKGnstoPBi8SDO6S4MeewLA+QBx5cureqa07CVvW14cZBEDsYJIOOORVY6j7QBmuBLbMh+EMzWwAMiBaIY4jDOaUftNxjsBAAmBbA7iTBXJk8yfOa05MDnWysmmXLrP7K97390IjZaWfdubaApFs4O0wY4MQRBmoumdftJuI1OovqG/eC+wiDbYwLfcNBHKxtJ4EmljThg0/EOTRHRv2cOffvcCOI/d7QdyMGQy3EQR3kMRQeKo7YIxt9F61XtsC4KIhtbZlSxcEDI8Xhx6c+dM7nXff2D7i7ZaPjt3lnchwRBIIP3mqbfsbmVxtXTkFUMbQFggHsvJPwqO3lQek1CWjuEuw7fCvGZPxEfQV3wYJqb0/5GyRXL5V/4WHoOgfS3xft8pmOAwPxBicAEYzxg9qk9sVSxcsnTmLV4G9bdcHxRAkfwgRHr61X7vUb2qMZYSMKu1PMQO/bJJ8pqz6Dpj3dC2ncBrlktd0577ebtoHz/ABDzPyrRCfJ1WgLQqtdUGpZ7FyE/aQqlgYUX1/w7n+UMSUYeVxvKmnsjqP2WyU1OmjxmXk7xJiDtMgDiBjPzNUPXLJJ5ny/vuM1edL1wXNMt26CxjZeOPiCzuaY+Nc/6g/lRn0On81lxBs62xcTeQGUqJyyhsYPcHH5VWm6CumBUWwX58XHbg9xSrQ9SbZutkgEZ7wP8x+XerZ0X2nssm244IH4WEjj8JNS5NaKPGpbOdPeVbaxaG+RJ/pRGoYnxEACjrX7LdWLb7DzBz+Rz+dQ9W6NqGX9y1th8+fvj86SfLtbFtQj0Vb2j6fcuQ1pN2IMFRHrk1WdQjWFm4hLcQIPxTtkiQJqxdR1t+1NnaouztksCEJAPi2E5giB/4IWi6zatD3b7r15ztk4A3mCpeCQAchlBPbwjFUwYZyjykv8Asks76KffOoullMW5BKqBnGY7mTBHbMUj27SZJJ9ab9S6k90khwneE3KPuF3E/Wk2oTZdKseDkggz3P61rceK6FUrewvQkiMxP9/1o9W3Sh5ZT+f+5n6UDbbxAAeRY+nkPrFddUfY6sORE/LI/rSD2LDgweZpmrRYHr/Un9BS7VPLk/3mitSSEQH+4H+9OhZ7cV+JDeudhQ105Arsmh7pyDQKSYZpm5pl094NKdOaY6J8iuHgyyaByHDDkgifPEifqBT6zrituSJzVY0rbGx8JOR5T+IU2uA+5AnvWfKthyvoZ6XqO84tjHyrKX9KvbGnmsqSolbLHqvZ8+894xdlXAClgJ7Erwf7xQmov3NOFGxSWMkFnTJgKq3EysckzHp5c6z26e6DtREHfaxYn6xApFf9r77mFdgOMAfqaVePJ1fX4kYqnsd3+g2dRdbUXNMykwx8SlHjkss8nvzJz3yRpP2ZFa0EsKuYVWMlm5hZ8IwOInyxVJ1WsvOxDM5HJljEeZAgUuy2RAA5jEfbNUlgcltlHJfYvV3qCWyZIAUZLHbkYEQZPaudN1jTEhWvQGido5xkMx7E/KKo1hQxhu/5VxpTF0DsOPoDSR8OK9itp+i/a66lwiygvC0vCWbtsMfU2roDuPLY59KH0vRCjq3vLRtwdu9XS7MjcCl2WBxmDBoVtMt+zG0Er8PpMHHzwfnNcftF0BN3iKREzmCYBPpReOSjUDnsvGutObX7tAzrESYHqee1V3rGifUWV3sguIZUmROMrAB/81afZ7XLftKSCGjIzg1L1RbSK1xtoC5aSB/c1njzUr9iUeZWem7oBkEfCfzIz5H++aZL0pjwO2SBH/il132kCk+6tIJJIL+LBJMBBjv3mlWs6nfvDx3HcD8P4fpbXwg+sVvUkMMtR7m2pXdvaCISGzxk8A/WlluPEoXBxmGPfzwOZntR/TfZ65c7EqOfKrL0j2eVLglMkRM+WYA7fPvikcr1dDpPtFc6Z0y7dEAFVEgM4zAj4R5fYGJ+dh0Xs9bsgs5a4fWD9hgfeas9npJxNMrfTFjIqPNLpF/hN7kygv1G6WCW0Fv5jc3fucD7VLptLqV1Kam0ZZSDknP8QPoRI+tFaqzt1xUcbj/21a+nlVtSfM/lTTnSsSEVbsoPtz0n3V331tSNPe8a4wjEw9skYDK048ojil3s3fW3f93dE2L21Lgz+JvAwjMq0H5FvOvWbVsXLe149zePcTDbSGEeZG0+Xgbzqiv0d9Pcvb1xahUn8W+SCGPICz9SO4NaIyUlYrjssfQvZ+5pzcKhSviChGLEAHA8yQBHegesdKW9LfA/8S4n/UO/60b7LdadbSiZKf4ik8z8LL6wCpk8oP4qe623a1Y3Wzsugd8B/Rv61nyQb69DS5RVxPLg9y0YcMp4DGYMeR4q09M1t425NwpvIW2YyxJg7ZIyMZ4zz2PXUrOxWGpQi2uWG3cceSg59I/3pD0f2ntXdVZRVFq0CBaF1EZsAxLGQrs4/TJqniR53KXonLO2qLGRpun2oVDca4Tve54mbZMkzgeJjwO55pPZ61pm3XGsKCo5BiWeQoAhMxubn8BpZ7a9YcXCht2jtVMFIyw3nKFcZFKv2y1csoht+7Z2LEoxIG2UQlHkkT7zAYc/SvTSVb7M7eyw6DoGk1NwC2SskeE+QycN6Yw5qie33SDY1RGCDBJGILS20g5BgjBr0D2Y6UbVl724OpU/BJPu18Tn3bAN4jAiO1UDrmta+zG5J5PMxJ7E9pIEfKpzV9DppLYos6oqO0/33/pXeoVrkMM+GD+vFLBIOf7/ALxTbpepKwD3rOyidggs4k4Ax6nHb+tTa2IBHnB+ox+hph1DSloYQV88Dv3oe7Z3bh6SB6066JSk1NWLQfKobmRXQNc3KBdk2mOKYaYzS7TDFGWo5/v7Vw8SyaWTt/I+Y7qf1FNmUe7UUq6W4KgwSRz658vP5U5K4AqGcpkV0c6W0JrKL0y5FZWOxKQr1GiCfBwxEennmg7qDcpAAg9v1p4tpvgcFZ4JxB7HNAPpAu73l22kYyw/IV6TM4F7sNuAPc0qW34ojNGXuqW7ZHu/3kCCeAT6dyKBv9UZsiEIONojB8zXHHaWGGYOD8v1qXUe7XIb94ONokH5nigH1LHPJMSTk/c1EHzzSuR2i16L2o2Wii2beB8TCW45JEd+1L73tHqGkgok5O22s/dpilFs9uKtHQvY6/qDx7tOd7j8lXkn5xUb47Kt86UV0AdI9obunuG5uLyI2sxI8wfTvxWX01Ouvb2Uu5GAoMKB5c7R8+81funf8OraT71vezxgoB/0tM8ZntVj0/TFQQsKB2GAPoKi5xTv2NHA/Z5vpfYZyQLrbO5Agk+hjEfWrNo/Z+xaYIqeM5BbM4njjt5Ubq74dh4C0cZIkescf71Lp1cGQBKg7AxmSVOCfLioSyzk9dEuaUtdB9u29vxgSe4H9KkOqBuKY2tBABHc0r6J1C4m/wB+WPigSRIPJIH8OR/Su+q9VQ3LRQMxycCO8d/WRQ5W7uhpcZ/NY31GqiF3ruPnj8+1QWtUsM1wn0C8kR6d6VavUo7qrRv8hzx3I7V3IzP2+XpU9uQXFvpleNzdq5AgEnB5HhPJp015dhRSDtkFn3AST2PECkWo/wDycDucAc+HiKkuaiBDTEyoYMpkcysD+xV86+VRf2JN0qLr0S8hsixd2uph1Kn5ER3BGKbdQ6Va1VtbdwsQpBBBAbHaYOD3/lXllrqb27gfcx3ZM9vIjtxXpPszrVvLIOf51fDOkkWVONoXazTaOwrpYQbwviIkmJBy79pgwD24qu379xQCDsc9p8LZ4B7H7U16upS/qQVZvDwJJIbbEefP5Uo2m6CbiFckLJyR6jtUsmaad1oXm4uu0V3/AIidRvagaayw+EFgSOWY7FG7iRDf9dIunMl7UWbV34AwBfMlFUwHA5nAxkT3gCnljrKC7dDgbZNtMYCgbSWXgjbAkZG/0rvp/Q1DHUrLIhBAEPPfwsvMYEEA5ntXqw+WKsk/mdoId7V5mt3zsuISqv7wBboXwhlLKQTiCJ9Y7Vjez9s6jYr4QKpkI+RlvgYH4i3aqNb1b22c5KkywBwTOD857880+6deslkvXWV3uMwZAAApaRuOPCJM+eBFU2vYun6Lt1voN/3Z9yVCQhZpIhVgKFUAn4vETAjzNVbqPR0Nvdfug3CxDGQGMBTlULFjLSSYOBNG3faJ7miv28gqNvu13R4nUERMsfikmq3+y3jbtgqyje58Q2CItAGWgRINcr6ZzaNe0PTLFu5sVTtCEgcZk92JNGaVtPYsWntWyC6XJm65yoYYjjkYFd+1mkRbrTcmEC+BS2Se+4qOCxwTxQgFr9ltj96xDXRwq8oDx4ppYxVBcnYk6tf33zcUbQ4DRMwY2tmByQT/AM1Yx71rUlIQKGBlp3EHGPICsoPsjLsW6y3DHyOf6/n/ACqE0y1KbhH2pWWg5+1IzRCVoYdG02/cPI/rT3T9EJ7mk/szeAukH8Q/T/zXonT7QIrNlk0zViSaJfZb2ftqwLDcZ/FkfY4oHT28CatXTFgikNlfKssm2NNUd6a1mtVKqkmt0UhKZ5prdXdumblx3+ZP6UOtnvUpJnFE6bQ3bgYpbdlX4iqkgfOK2c2ZqYJsrZTyq+9D/wCHD3FV7933QOdgEtHqSYB+9XHQewuhtwRa94wIO64S2Rx4fh/KpPKiixSZ5H0z2e1Goj3dtiD+I+FR/wAx5+k1deg/8NUKhtTdYGZKWojB7uQZkeQHNek2ra9gMYx2ogKPIVN5GyyxRQkToWls2m91bVfDzyTHmTk1v2XUe4HnJ/WmmtQe7b5GlXsw4GnB9T+tL6G9je6pAJUSewnmkljqdsjddJtt4twzAjjPfH50F7VM1wgBiEA7GADPJNJLFq7ZRg6s1phhjwpg4k9jn7VnlJciGTK1KkOrXUkmQdyTggQwGJkHymo+pe0KopS2sT8LnOSc4pLp9b71D7pCEWTvUFhA+IkjA+X+9cPcmAVVu4OD+VI5uLpMz8nWhjqNUq2ffXQYXLQSCciAvqeKi03tDba+t1Q1s7d+wAEBQGDyeBMcg4ic0q6onvUNu88CYnGADyB2JxkCcR3pdpenEWmCuNltmDu/hBtsQV5yPxeGrKEXCktjR2Mtb1/ZdDAbi0ifLPc8eWfTtU96xqLqswvMLf4SgCiIE73HB+tV72fsW0uN4b11QCJUGCxiFABMLB/EZwMZqz6fqNzUWWQILLIQuyX28ZkKV3DnmeKnLG8bqP6sd0gPTLBG3xETG07pMYAMmZpfreo6xQFu2zbEsVwCzYzLcYB4+VM+h6NVDb3YFWMHEeQYsvBkjyH6V11DVkyt3ab4t/u2jmO8fCcg8j/fTOePkk9ichJ0vV6u9FlFzPxkcfU4q7ezPvNMwDxExIJz/qU8GZjzio9V1gtp0YCC6nbc2kw0xG7t9Qfyoa11Ym5buMkGVDI0Z2tkQfiyMfSllkjaUUGM+LPReqdMN8JcQ7XiD6ryPz/U1TeqP7u4GaQQYIGJwR344OfSrXoOqW9SWXDoQuCAQQyhsrH+YjNUj2o9xpzIuq+nVkB2tuZAYRVMkzkCD60+bE5NOHZ00+zzjV2GdvCZuCdyD4idxyo/FPcDM9o4YabqjaWEI4MMMrJBDNJGQQ0AHtB86K1PS2u37moCjYTuX+HcTtUT6QT9jVd6xrjcfbcZiFwjHxEAT91J9ew9Z9TsToadZ11l7ZJWHuPMlVnaCQPGkHJLcg/CKH1vQmt2keQLbk+JvCBABEjzPigCZAEUp1Wn3XAodWMAQA3YZGRzz9aM671/fZXTQCluNnbxfiOMEZYDyk5zXddHd9hl/X2yrJYdi7hWuNMSR8YCgYG7OSZxxW7PTLrm0AjGVnCsebj948gKF9njbt/vCYdFYx4hJ2kcgcZjkcU8PtKwugbUMBOQzfgWfiYjkHt3pk2wUvYy9regMbhkwWZYEFvgtiZ2cGXqS57OImi3XHiHb8IXlFHNwikft5r2u6qcmAIkcdoEYHw8URrbV39hXwGNxJO3AEuJJOAIUZoK67C6sqvUUUXiqGVUATjOJPwkjvH0qMmhrbySfMz96l3UpJ9kgFB6rTg+U/Oix51G18H/AMTQOTadoWWSUZW4II/v7V7F7PJKKfSvLfdruWBuLMAO3Jj7f351670e2EQDyFZfI9HoeO7Vh8bXWO5pPctlCRGQSD8wYNOrZE7j/YpLcubmYnuSfuZrKUyeiS1WV0oOKymtE7G/TfYvR2iT7rfP/wCzxR8hTzQ6G3aXbbRUXsFAA/Ki1Su2j0pdvsqqXQn6t1hLJCldzRMcYz388cUI3WBetldpXcMwZECJBMCDniMjv2pb7Wm0t7xsFZwCCQYEADxNI5ggRPaYqs2vaTYwQCIPIO5Y/X9fOahJzT0ZMmSVtFgv6x7MFGI2sW55kKCD6GKtb9SG1TzIBleDInHpVZ0bpfZkuW2ERtwQYOQfEBEZkEeXM0xuXAgLGDtI8PnkCJroyqNs7FPjdknUOpEq0GBBpV0i9KbQwwcgH+VNF1yuSFG0RmIjGPLPNKl0BLG5bWJziIx/I80XN9HPNbJNVbDqVOQeeD/4Pr2oU2FSCWxwN548h5T2msu6+3Y0uy4SrKTI/EcysgZJj6YqtattRrgxt+7WzbIMPcVS5ALRkZMA4wPnTrDyVh53uiXWdWt2b5/YluLvhSHI2lgchrYHnx3y2ROJOta5veuQoABbwjBhSADtjdmeZjGOYoTTdNa66XbgVFLKxbdywILBQD8WDgg/EOIoQ3rupgJiMtcIMhWIgCPOCQoknyGSA4W0mhaLPo7AdUYAtuXxq3rx8oIPHcClntFYUjc28pblShiAdu4MoWAXwZLT5/PXS9Y9g7fdzaJ8wrAGAWmck8n7dppjpdcoLbzun+LhuTkARjH/AE0L4PRO6Yo6FaMuRbFq3cAACjbJUhlaYyZJM/OpheYPcRiYaAB5xIP+9WA6osCIBB7R+RA7zVd1NsklgW2kkeEZB8pJxgc+tdOUZO0B7Dtu0LuYAHESJPniRJ/rRSn3gba9vwx4YBgE4GyBmI4JGKVJ0IEq8jbb8Sruac91Iwc8jHH0pv06QCZxxn6/zBHzpJxSh9wpasXHR+5lnd0UAear8oWB9K6/9SuMBtuBcCJAYjEyQASMEf2aO1N1VuLKhhxHiESR+NT4OQciOZxJCLqoyrW1jxQ53A42wARAKk4yfXzUnlUop1sommuhrqNPcsWAZZPfBUYquAzxEAcqcgkZg4Hmh1T7FNtrXvbJBMkna+J323XgDn/uHYOuuaO+thLZulkC7lUEsAySqgE5lfLgziqr0Cw133lsGNw8/DM7pI4JhIE+det4U0sX6k5Jt0x/7Pe0S2NIVPi5C8BvETGDgwsmDwS0GkB0Nu+xe3tUINxWNox8IIztJMDyM/OoOr6dEPuw+2BI3SZ3QZYqMEjPEZ7RS5veWoEnxQZU4M/CAynyMx6+laK+wb9MZr0W6i+9WS5YBdu6ZMZBjzIyOPrSEWdtza4lQczzA8vIwKd6fX3bT+IZiTuE5IKrIbMiWPnxWNdt3iZG07THlnwiCf8AV8Jx5Ghvs516AtJaG123AiANskN4mA4iPtNGtqrfvmItfibBc+Zj4QKO6R0QKC11gFDLncomJc4IJ+FDiKI6N02w91R70ZZR8aCdzAd0prQOLYJ7S33/AGy5tcqA0AKxUAQOBOO/qe+Zpn7QbzpLW5ifBuySf/jDH/vrrqvXh+13lCztuOqkPzDlR+D5U19vOvg6b3YX4ldPjJj4E4AAPB5oW9aOpUzzGylF7go4k9hQ2neigwBwNzfpQIsi9yznxceVTbADtXn0/v8AWpRJwD828vQV3btKo4mfM8+rHyrqFsJ6NpgbimBgzI848zzXoOmueECqd0djIH9/+Kten4rF5H1HpeIv9Ow3UXPDS+1Yzk0Q7edcgCsrexsst0SJPlisraMTWULJWXXdFC39cOBk0tu6styTQmp1AVd0E5wB613O+i8nSOuo2bTn3l5ATIEwWyOBHegr2sRFJtWkUgeHCk/Lw5HeodXq3cgWhDYyeQO/pH9ah1mlIUEMd34vxA+cz4s+c0G3FaMkvmbaDui9RW4WZvJccfxdx8vyNb12ot4QloORkZAzx8Rj+XNILN5hcRU7njAnkkdvL70v6jp919rg3MN0zPyx8v5YpealERXQ90vUUuGAdiiRJWfXIn5d6kfrNzC2U96wDSWO1fJYUjJHJExn60h3Lt8PxcntnMyJrnSdXVCV3PA7AcnykkRxzSQW+gIhvdMvSGdSbpmTyeZ54mSaN2OqG4bYYH4irBVBmNoLTwRH0oxusNhl8Vs4YEeJc+mSMH0M+Wan6R0ezesi26naoYrtYgiTJgggGfXn6Vbnb2FyvTKtq+pIhhANwJ4IYAkMp8Q5weR3+VWPoVxxaQsTuMll2wM9jImcTPrzXA9nLFsm4tt3MyqFgYjyBEkj680602iLHBEtkA8jE58jVU8T9jckwW70dXZmJwckTn5Ukv6jZ4UUqCeSJxEiAQQMj5me1WDWaaU+PaciOc59RHYUvbou0qVAYMdsuAWjJJjIH0zUMkIJ/KxdHPTdS7W/ebwWBKxBhYzx54mc/qKP0t0kE3NoYnBAkMBGSAecESO0VA+gGmuhvdqVMNwDuCmSGJX4hzPr86WdQ1cYRgohZI7SMwDO2SD6YxAipTi07Qzj7RYLlkyoRVKH4oIHOZjHfyofUqphwCQCCY7f5vziBzj0NItHqACIuqysBMNmBJMq2eJ486tPSrga3KtbgCMupPEeMDj6TQhBxbTEaBm0g9/4crtUt3ByZ/IdvU96k1vT7QR2JQLt8SNwV7gsefKPzpN1DqrK0WthHaAYOM7GmI+hpNrNfdK+O6w9E2iYM+IbSMQOJ/lVoYpS7SHjB9kmt10lgj4EsCrEqGYwJicT5xG7EYqP3z27b29TZa1dZN1p2UmSs7Srr/mzGe3E019kOhBYvXVOPgSTiRlmzJPofr5Vaeqe7v2PdtF1XBIgmMGQQRBUrj1HFbcUVjVWM/wPIrAbUPPxGSW4kj4if1wKHW1cUs53KPxciTPHrJxFD2XcZViJ/vip0DOQGPy8p+n61s5MjyXZl8NDznP5qO0fOpnskWQyENv8TRyqrgBl5AJk+WFzTr3yfsyi7LMbhJM5iDPrxtEjy4pFdRVfwHGTgnGcQSAaZDd7Q/tu76HLf/IxEsowLL2+WI7uaC9lbLnUWoIPjB+ND8Pi8/Sm2ps3G0gtbQIyYVFkj4iWxP8Aid6H9kug3Gu/DMA8FTkkAcGuvR1bBdL7ttUd3vJN7MFefeEn+fepfbe/bGxU3SROQowWduxyfhpx0Dolo3wfeCQxMRa7Kx//AGelV7292LqhbRtwS2gJheWXd+EkcEHnvQbVnNNRENlsetH2EjA+poa0x8zFTpcziuIsNUAcVrzY+WP7/vtWg1c6i5Ck+VcJQ29nDudh5R/P+lW+3gVWfYTTE2nc93x8gB/vVkuDMCsGV3Jnr4Y8YJEm/NTiPIUGTOD+VSKY74qLjZOUbdhgjGayoUE1lLxRNjEd6A6mY2Adw5PqQVArKypf2v8AIbP0asCFWPIVtviH+oVlZTw6Q66QF7TWl9zbbaJLwTAkxasESfqfuaR6Ey4BzkfzrKyh/umWf1EF4Q4jGF4+tcX0G44H9itVldL6wMdezCDOBkiccwTE1YumWwqXQoCiRwI/+MHt6kn61lZQXYoH1v8AwEPcd+/fvWtIcW/9K/oKysrPl+kAVcUZx+H/AO1TdJ+If6f5rWVlPi6Rwx6mgOnMgGQQfUFTIPpgfavJ9xNt5M5t/wAq1WVd9/sXh0LuhOff2xJgEwOww3ApraxqiBgBRAHAlyDA7SAPtWVlaJ/3fkF9lg6jbHuNRgYQEY4O1TI9ZJ+5pP0dQdUsgY3EehEEEes1qsoeN1+oF0Xez/ht/wA/86A9mB/7dPSQPQcwPIVlZTZ/Q8fpZ5ha4Hyoj+n8jWVlegYGddYOF+v6JQ/T2P7Rp8n4h/3Gt1lGXRbH6PXPae2FsEqADtu8COGxxSv/AIaHe77vFAtxuzHjPE1lZUf7DQu2VD2X/wAUfJv/AObUg65/+Rc+Y/7RWqyr5DKujizxU1vmtVlKKwsc/Sotef3Z+VZWVwsey8+wg/8AZr/qb/uNNbnf61lZXn5PqZ68foX5ANj4jR+gEuJ86yspfRNBLfGaysrKmRfZ/9k=" alt="Imagen 2" /></a>
    <a href="#"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQaNEoqOkfFGAvi10HKTFoSX3Bx4RUozB5AVA&s" alt="Imagen 3" /></a>
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
        {icon:"https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000", title:"Seguridad", desc:"Protección con login, cifrado y control de usuarios."}
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
        {icon:"https://img.icons8.com/?size=100&id=Ykiu3xrXkppF&format=png&color=000000", title:"Security", desc:"Protection with login, encryption, and user control."}
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
