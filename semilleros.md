---
layout: single
title: "Semilleros GIDA"
permalink: /semilleros/
author_profile: true
header:
  overlay_color: "#05070a"
  caption: "Formación y Divulgación Aeroespacial"
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  header.page__hero--overlay, .page__hero--overlay {
    position: relative !important;
    background-color: #05070a !important;
    overflow: hidden;
  }
  .page__hero-content, .wrapper { position: relative; z-index: 5; }

  /* TABLA DE PROGRAMACIÓN */
  .tabla-semillero {
    width: 100%;
    border-collapse: separate;
    border-spacing: 0;
    border-radius: 10px;
    overflow: hidden;
    margin: 30px 0;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  }
  .tabla-semillero th {
    background: #950001;
    color: white;
    padding: 15px;
    text-align: left;
  }
  .tabla-semillero td { padding: 12px 15px; border-bottom: 1px solid #eee; }

  /* GRID DE YOUTUBE */
  .yt-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 25px;
    margin-top: 20px;
  }
  .yt-card {
    background: #fff;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0,0,0,0.08);
    transition: 0.3s;
    border: 1px solid #eee;
    display: flex;
    flex-direction: column;
  }
  .yt-card:hover { transform: translateY(-5px); border-color: #ff0000; }
  .yt-thumb {
    width: 100%; height: 160px;
    background-size: cover;
    background-position: center;
    display: flex; align-items: center; justify-content: center;
  }
  .yt-overlay {
    background: rgba(255,0,0,0.8);
    color: white; padding: 4px 10px;
    border-radius: 4px; font-size: 0.75em; font-weight: bold;
  }
  .yt-info { padding: 15px; flex-grow: 1; }
  .yt-title { font-weight: bold; color: #333; text-decoration: none; font-size: 1em; display: block; margin-bottom: 5px; }
  .yt-desc { font-size: 0.85em; color: #666; line-height: 1.4; }
  
  .btn-yt {
    background: #ff0000; color: white !important;
    padding: 12px 25px; border-radius: 30px;
    text-decoration: none; display: inline-block;
    font-weight: bold; margin-top: 30px;
  }
</style>

El semillero es el espacio donde la academia se encuentra con la pasión por el espacio. Aquí compartimos el conocimiento técnico necesario para impulsar la cohetería experimental en Colombia.

## 📅 Próximas Sesiones Presenciales
*Las fechas se actualizan semestralmente según el calendario académico.*

<table class="tabla-semillero">
  <thead>
    <tr>
      <th>Fecha</th>
      <th>Tema</th>
      <th>Conferencista</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Por definir</td><td>Introducción y Bienvenida</td><td>Líderes GIDA</td></tr>
    <tr><td>Por definir</td><td>Principios de Propulsión</td><td>Área de Motores</td></tr>
    <tr><td>Por definir</td><td>Diseño y Simulación</td><td>Área de Estructuras</td></tr>
    <tr><td>Por definir</td><td>Electrónica y Telemetría</td><td>Área de Control</td></tr>
    <tr><td>Por definir</td><td>Lanzamiento Experimental</td><td>Equipo de Logística</td></tr>
  </tbody>
</table>

---

---
## 📺 Listas de Reproducción
Cursos y memorias audiovisuales de nuestras actividades académicas.

<div class="yt-grid">
  <div class="yt-card">
    <div class="yt-thumb" style="background-image: url('{{ "/assets/images/image_1f2be0.jpg" | relative_url }}');">
       <div class="yt-overlay">CURSO</div>
    </div>
    <div class="yt-info">
      <a href="https://youtube.com/playlist?list=PL0mmfoegIHGHQWsowK9Hx19bnTQfqui2_" class="yt-title" target="_blank">Semillero en Ciencias Aeroespaciales</a>
      <p class="yt-desc">Bases fundamentales para el estudio y desarrollo de proyectos aeroespaciales.</p>
    </div>
  </div>

  <div class="yt-card">
    <div class="yt-thumb" style="background-image: url('{{ "/assets/images/image_1f2c41.jpg" | relative_url }}');">
       <div class="yt-overlay">VIRTUAL</div>
    </div>
    <div class="yt-info">
      <a href="https://youtube.com/playlist?list=PL0mmfoegIHGHAAnS6AEuBmgbk2mMV4gIF" class="yt-title" target="_blank">Introducción a la Ciencia y Tecnología</a>
      <p class="yt-desc">Curso virtual detallado sobre los pilares de la ingeniería espacial.</p>
    </div>
  </div>

  <div class="yt-card">
    <div class="yt-thumb" style="background-image: url('{{ "/assets/images/image_1f2f2c.png" | relative_url }}');">
       <div class="yt-overlay">MEMORIAS</div>
    </div>
    <div class="yt-info">
      <a href="https://www.youtube.com/playlist?list=PLW-x_Z6ObeI0Vp7X7u_eS_L-v0YV_mPZ4" class="yt-title" target="_blank">GIDA Feria y Exhibiciones</a>
      <p class="yt-desc">Registros de ferias, entrevistas y lanzamientos de cohetes de agua grabados.</p>
    </div>
  </div>
</div>

## 🎥 Contenido Adicional Destacado
Entrevistas y material especial con expertos internacionales.

<div class="yt-grid">
  <div class="yt-card">
    <div class="yt-thumb" style="background-image: url('https://img.youtube.com/vi/0lkiC00OgKE/0.jpg');">
       <div class="yt-overlay">DESTACADO</div>
    </div>
    <div class="yt-info">
      <a href="https://youtu.be/0lkiC00OgKE" class="yt-title" target="_blank">Entrevista Jacky Silva-Martínez</a>
      <p class="yt-desc">Conversación desde el Johnson Space Center de la NASA sobre su trayectoria y el futuro espacial.</p>
    </div>
  </div>
</div>
## 🎥 Contenido Adicional Destacado
Entrevistas y material especial con expertos internacionales.

<div class="yt-grid">
  <div class="yt-card">
    <div class="yt-thumb" style="background-image: url('https://img.youtube.com/vi/0lkiC00OgKE/0.jpg');">
       <div class="yt-overlay">DESTACADO</div>
    </div>
    <div class="yt-info">
      <a href="https://youtu.be/0lkiC00OgKE" class="yt-title" target="_blank">Entrevista Jacky Silva-Martínez</a>
      <p class="yt-desc">Conversación desde el Johnson Space Center de la NASA sobre su trayectoria y el futuro espacial.</p>
    </div>
  </div>
</div>

<center>
  <a href="https://youtube.com/@gidaun" class="btn-yt" target="_blank">
    <i class="fab fa-youtube"></i> SUSCRÍBETE AL CANAL
  </a>
</center>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    const canvas = document.getElementById('canvas-estrellas');
    const ctx = canvas.getContext('2d');
    const header = document.querySelector('.page__hero--overlay') || document.querySelector('header');
    const container = document.getElementById('mi-header-espacial');

    if (header && container) {
      header.appendChild(container);
      function resize() {
        canvas.width = header.offsetWidth;
        canvas.height = header.offsetHeight;
      }
      let stars = Array.from({length: 120}, () => ({
        x: Math.random() * window.innerWidth,
        y: Math.random() * 400,
        r: Math.random() * 1.5,
        v: Math.random() * 0.4
      }));
      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "white";
        stars.forEach(s => {
          ctx.beginPath(); ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2); ctx.fill();
          s.y += s.v;
          if (s.y > canvas.height) s.y = 0;
        });
        requestAnimationFrame(animate);
      }
      window.addEventListener('resize', resize);
      resize(); animate();
    }
  });
</script>