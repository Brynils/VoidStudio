<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Void Studio 3D</title>
<style>
* { margin:0; padding:0; box-sizing:border-box; font-family:sans-serif; }

body {
  background-color:#111;
  overflow:hidden;
  transition: background-color 0.3s linear;
}

/* Logo inicial */
#intro-text {
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  font-size:5rem;
  font-weight:bold;
  color:#fff;
  cursor:pointer;
  transition: all 1s ease, color 0.5s ease;
  z-index:10;
}

/* Franja superior */
#menu-bar {
  position:fixed;
  top:0;
  left:0;
  height:60px;
  width:100%;
  background-color:#000;
  display:flex;
  align-items:center;
  padding-left:250px;
  justify-content:space-between;
  opacity:0;
  visibility:hidden;
  transition:opacity 1s ease;
  z-index:5;
}

/* Pestañas de navegación */
.nav-tab {
  color:#fff;
  text-decoration:none;
  margin-right:30px;
  font-size:1rem;
  opacity:0;
  transition: opacity 0.5s ease, transform 0.3s ease;
  padding:5px 10px;
  border-radius:5px;
  display:inline-block;
}

.nav-tab:hover {
  transform: scale(1.3);
  z-index:10;
}

/* Menú hamburguesa social */
#social-menu {
  position:relative;
  margin-right:20px;
}

#social-menu button {
  background:none;
  border:none;
  cursor:pointer;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  width:25px;
  height:18px;
}

#social-menu button span {
  display:block;
  height:3px;
  width:100%;
  background:#fff;
  border-radius:2px;
}

#social-menu .dropdown {
  display:none;
  position:absolute;
  top:25px;
  right:0;
  background-color:#111;
  border-radius:5px;
  overflow:hidden;
  flex-direction:column;
  min-width:150px;
  z-index:10;
}

#social-menu .dropdown a {
  color:#fff;
  padding:10px;
  text-decoration:none;
  display:flex;
  align-items:center;
  gap:10px;
}

#social-menu .dropdown a img {
  width:20px;
  height:20px;
  filter: grayscale(100%);
  transition: filter 0.3s ease;
}

#social-menu .dropdown a:hover img {
  filter: grayscale(0%);
}

/* Contenido principal */
#main-content {
  opacity:0;
  visibility:hidden;
  transition:opacity 1s ease;
}

/* Carrusel */
#carousel {
  width:90%;
  max-width:1200px;
  height:500px;
  margin:120px auto 0;
  position:relative;
  overflow:hidden;
  border-radius:10px;
  box-shadow:0 5px 15px rgba(0,0,0,0.2);
  opacity:0;
  transform:translateY(-50px);
  transition: all 1s ease;
}

.slide {
  position:absolute;
  width:100%;
  height:100%;
  background-size:cover;
  background-position:center;
  opacity:0;
  transition: opacity 1s ease;
}

.slide.active { opacity:1; }

.arrow {
  position:absolute;
  top:50%;
  transform:translateY(-50%);
  background-color: rgba(0,0,0,0.5);
  color:#fff;
  border:none;
  width:45px;
  height:45px;
  border-radius:50%;
  cursor:pointer;
  font-size:1.5rem;
}

.arrow:hover { background-color: rgba(0,0,0,0.8); }
.arrow.left { left:15px; }
.arrow.right { right:15px; }

.dots {
  position:absolute;
  bottom:15px;
  width:100%;
  text-align:center;
}

.dot {
  display:inline-block;
  width:12px;
  height:12px;
  margin:5px;
  border-radius:50%;
  background-color:#000;
  cursor:pointer;
  transition: background-color 0.3s ease;
}

.dot.active { background-color:#fff; }

/* Secciones */
.section {
  width:80%;
  max-width:1100px;
  margin:150px auto;
  opacity:0;
  transform:translateY(60px);
  transition: all 0.8s ease;
}

.section.visible {
  opacity:1;
  transform:translateY(0);
}

.section h2 {
  font-size:2rem;
  margin-bottom:20px;
}

/* Proyectos */
.project {
  display:flex;
  align-items:center;
  background-color:#f4f4f4;
  border-radius:10px;
  padding:20px;
  margin-bottom:20px;
  gap:20px;
  cursor:pointer;
  overflow:hidden;
  position:relative;
}

.project img {
  width:180px;
  height:120px;
  object-fit:cover;
  border-radius:10px;
  transition: transform 0.3s ease;
}

.project:hover img { transform: scale(1.05); }

.project-info {
  flex:1;
}

.project-info h3 { margin-bottom:10px; }
.project-info p { color:#555; }

/* Contacto */
#contacto {
  text-align:center;
  background-color:#000;
  color:#fff;
  padding:80px 20px;
  border-radius:20px;
}

#contacto h2 { font-size:2rem; margin-bottom:20px; }
#contacto p { margin:10px 0; font-size:1rem; }
#contacto a { color:#fff; text-decoration:none; font-weight:bold; }
#contacto a:hover { text-decoration:underline; }

</style>
</head>
<body>

<div id="intro-text">Void Studio 3D</div>

<div id="menu-bar">
  <div>
    <a class="nav-tab" href="interiores.html">Diseño de interiores</a>
    <a class="nav-tab" href="stands.html">Diseño de stands</a>
    <a class="nav-tab" href="comerciales.html">Espacios comerciales</a>
    <a class="nav-tab" href="eventos.html">Eventos y activaciones</a>
    <a class="nav-tab" href="mobiliario.html">Diseño mobiliario</a>
    <a class="nav-tab" href="automotriz.html">Diseño automotriz</a>
  </div>

  <!-- Menú social -->
  <div id="social-menu">
    <button id="social-btn">
      <span></span>
      <span></span>
      <span></span>
    </button>
    <div class="dropdown">
      <a href="https://instagram.com/voidstudio3d" target="_blank"><img src="https://img.icons8.com/ios-glyphs/30/ffffff/instagram-new.png"/> Instagram</a>
      <a href="https://facebook.com" target="_blank"><img src="https://img.icons8.com/ios-glyphs/30/ffffff/facebook-new.png"/> Facebook</a>
      <a href="https://linkedin.com" target="_blank"><img src="https://img.icons8.com/ios-glyphs/30/ffffff/linkedin.png"/> LinkedIn</a>
      <a href="https://workana.com" target="_blank"><img src="https://img.icons8.com/ios-glyphs/30/ffffff/workana.png"/> Workana</a>
    </div>
  </div>
</div>

<div id="main-content">
  <!-- Carrusel -->
  <div id="carousel">
    <div class="slide active" style="background-image:url('https://picsum.photos/1200/500?1');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?2');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?3');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?4');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?5');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?6');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?7');"></div>
    <div class="slide" style="background-image:url('https://picsum.photos/1200/500?8');"></div>

    <button class="arrow left">‹</button>
    <button class="arrow right">›</button>

    <div class="dots">
      <span class="dot active"></span>
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
    </div>
  </div>

  <!-- Proyectos -->
  <section class="section" id="proyectos">
    <h2>Proyectos destacados</h2>
    <div class="project" data-images="https://picsum.photos/200/150?1,https://picsum.photos/200/150?11" onclick="window.location.href='proyecto1.html'">
      <img src="https://picsum.photos/200/150?1" alt="Proyecto 1">
      <div class="project-info">
        <h3>Diseño interior moderno</h3>
        <p>Espacio contemporáneo con materiales naturales y una atmósfera acogedora.</p>
      </div>
    </div>

    <div class="project" data-images="https://picsum.photos/200/150?2,https://picsum.photos/200/150?21" onclick="window.location.href='proyecto2.html'">
      <img src="https://picsum.photos/200/150?2" alt="Proyecto 2">
      <div class="project-info">
        <h3>Stand para evento</h3>
        <p>Estructura innovadora que resalta la marca y optimiza la experiencia del visitante.</p>
      </div>
    </div>
  </section>

  <!-- Contacto -->
  <section class="section" id="contacto">
    <h2>Información de contacto</h2>
    <p>Email: <a href="mailto:voidstudio3d@gmail.com">voidstudio3d@gmail.com</a></p>
    <p>Teléfono: <a href="tel:+59170000000">+591 700 00000</a></p>
    <p>Instagram: <a href="https://instagram.com/voidstudio3d" target="_blank">@voidstudio3d</a></p>
    <p>Ubicación: Cochabamba, Bolivia</p>
  </section>
</div>

<script>
window.addEventListener('load', () => {
  const introText = document.getElementById('intro-text');
  const menu = document.getElementById('menu-bar');
  const links = menu.querySelectorAll('.nav-tab');
  const mainContent = document.getElementById('main-content');
  const carousel = document.getElementById('carousel');

  introText.addEventListener('click', () => {
    document.body.style.overflowY = "auto"; 
    introText.style.position = 'fixed';
    introText.style.top = '17px';
    introText.style.left = '30px';
    introText.style.transform = 'translate(0,0)';
    introText.style.fontSize = '1.5rem';

    setTimeout(() => {
      menu.style.opacity = '1';
      menu.style.visibility = 'visible';
      mainContent.style.opacity = '1';
      mainContent.style.visibility = 'visible';
      carousel.style.opacity = '1';
      carousel.style.transform = 'translateY(0)';
      links.forEach((link,i)=>{ setTimeout(()=> link.style.opacity='1', i*200); });
    },500);
  });

  // Carrusel
  const slides = document.querySelectorAll('.slide');
  const dots = document.querySelectorAll('.dot');
  const prev = document.querySelector('.arrow.left');
  const next = document.querySelector('.arrow.right');
  let index = 0;

  function showSlide(i){
    slides.forEach(s => s.classList.remove('active'));
    dots.forEach(d => d.classList.remove('active'));
    slides[i].classList.add('active');
    dots[i].classList.add('active');
  }

  next.addEventListener('click',()=>{ index=(index+1)%slides.length; showSlide(index); });
  prev.addEventListener('click',()=>{ index=(index-1+slides.length)%slides.length; showSlide(index); });
  dots.forEach((dot,i)=>{ dot.addEventListener('click',()=>{ index=i; showSlide(index); }); });

  // Carrusel automático cada 4s
  setInterval(()=>{ index=(index+1)%slides.length; showSlide(index); },4000);

  // Aparición por scroll
  const sections = document.querySelectorAll('.section');
  const observer = new IntersectionObserver(entries=>{
    entries.forEach(entry=>{ if(entry.isIntersecting) entry.target.classList.add('visible'); });
  }, { threshold:0.2 });
  sections.forEach(sec=>observer.observe(sec));

  // Previsualización proyectos
  const projects = document.querySelectorAll('.project');
  projects.forEach(p=>{
    const imgs = p.dataset.images.split(',');
    let imgIndex=0;
    let interval;
    p.addEventListener('mouseenter', ()=>{
      const imgEl = p.querySelector('img');
      interval = setInterval(()=>{
        imgIndex=(imgIndex+1)%imgs.length;
        imgEl.src = imgs[imgIndex];
      },1500); // más lento
    });
    p.addEventListener('mouseleave', ()=>{
      clearInterval(interval);
      const imgEl = p.querySelector('img');
      imgEl.src = imgs[0];
      imgIndex=0;
    });
  });

  // Social menu
  const socialBtn = document.getElementById('social-btn');
  const dropdown = document.querySelector('#social-menu .dropdown');
  socialBtn.addEventListener('click', ()=>{ dropdown.style.display = dropdown.style.display==='flex'?'none':'flex'; });
  document.addEventListener('click', e=>{ if(!socialBtn.contains(e.target) && !dropdown.contains(e.target)) dropdown.style.display='none'; });

  // Fondo cambia al scroll
  window.addEventListener('scroll', ()=>{
    let scroll = window.scrollY;
    let color = Math.min(scroll/800,1)*255;
    document.body.style.backgroundColor = `rgb(${color},${color},${color})`;
  });
});
</script>

</body>
</html>
