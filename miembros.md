---
layout: single
title: "Miembros del GIDA"
permalink: /miembros/
author_profile: true
header:
  overlay_color: "#05070a" 
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }
  .seccion-titulo { border-bottom: 2px solid #950001; margin: 50px 0 30px; color: #2c3e50; font-size: 1.8em; font-weight: bold; }
  
  /* CONTENEDOR DE LA REJILLA */
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); 
    gap: 30px;
    perspective: 1000px; /* Necesario para el efecto 3D */
  }

  /* ESTRUCTURA DE LA TARJETA FLIP */
  .member-card-container {
    width: 100%;
    height: 380px; /* Altura fija para consistencia */
    cursor: pointer;
  }

  .member-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border-radius: 12px;
  }

  /* Clase que activa el giro al hacer click (manejada por JS) */
  .member-card-container.is-flipped .member-card-inner {
    transform: rotateY(180deg);
  }

  .card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 12px;
    background: #ffffff;
    border: 1px solid #e1e1e1;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }

  /* PARTE FRONTAL */
  .member-img { width: 100%; height: 220px; object-fit: cover; }
  .info-front { padding: 15px; flex-grow: 1; display: flex; flex-direction: column; justify-content: center; }

  /* PARTE TRASERA */
  .card-back {
    transform: rotateY(180deg);
    background: #f9f9f9;
    padding: 20px;
    color: #333;
    text-align: left;
  }

  .scroll-content {
    overflow-y: auto; /* Habilita el scroll si el texto es largo */
    height: 100%;
    font-size: 0.9em;
    line-height: 1.5;
    padding-right: 5px;
  }

  /* Personalización del scrollbar */
  .scroll-content::-webkit-scrollbar { width: 4px; }
  .scroll-content::-webkit-scrollbar-thumb { background: #950001; border-radius: 10px; }
</style>

<h2 class="seccion-titulo">Estudiantes de Pregrado</h2>
<div class="team-grid">
  {% assign pregrado = site.data.miembros | where: "tipo", "pregrado" %}
  {% for miembro in pregrado %}
  <div class="member-card-container" onclick="this.classList.toggle('is-flipped')">
    <div class="member-card-inner">
      <div class="card-front">
        <img src="{{ miembro.foto | relative_url }}" class="member-img">
        <div class="info-front">
          <div style="font-weight:bold; font-size: 1.1em;">{{ miembro.nombre }}</div>
          <div style="color:#d35400; font-weight:bold;">{{ miembro.area }}</div>
          <div style="font-size:0.85em; margin-bottom: 5px;">{{ miembro.carrera }}</div>
          <a href="mailto:{{ miembro.correo }}" style="font-size:0.8em; color:#2980b9;">{{ miembro.correo }}</a>
        </div>
      </div>
      <div class="card-back">
        <div class="scroll-content">
          <strong style="color:#950001;">Descripción:</strong><br>
          {{ miembro.descripcion | default: "Integrante apasionado por la ingeniería aeroespacial y el desarrollo tecnológico en el GIDA." }}
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<h2 class="seccion-titulo">Estudiantes de Posgrado</h2>
<div class="team-grid">
  {% assign posgrado = site.data.miembros | where: "tipo", "posgrado" %}
  {% for miembro in posgrado %}
  <div class="member-card-container" onclick="this.classList.toggle('is-flipped')">
    <div class="member-card-inner">
      <div class="card-front">
        <img src="{{ miembro.foto | relative_url }}" class="member-img">
        <div class="info-front">
          <div style="font-weight:bold; font-size: 1.1em;">{{ miembro.nombre }}</div>
          <div style="color:#2980b9; font-weight:bold;">{{ miembro.area }}</div>
          <div style="font-size:0.85em; margin-bottom: 5px;">{{ miembro.carrera }}</div>
          <a href="mailto:{{ miembro.correo }}" style="font-size:0.8em; color:#2980b9;">{{ miembro.correo }}</a>
        </div>
      </div>
      <div class="card-back">
        <div class="scroll-content">
          <strong style="color:#2980b9;">Investigación:</strong><br>
          {{ miembro.descripcion | default: "Investigador enfocado en áreas avanzadas de la tecnología aeroespacial y soporte académico al grupo." }}
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<h2 class="seccion-titulo">Egresados</h2>
<div class="team-grid">
  {% assign egresados = site.data.miembros | where: "tipo", "egresado" %}
  {% for miembro in egresados %}
  <div class="member-card-container" onclick="this.classList.toggle('is-flipped')">
    <div class="member-card-inner">
      <div class="card-front">
        <img src="{{ miembro.foto | relative_url }}" class="member-img">
        <div class="info-front">
          <div style="font-weight:bold; font-size: 1.1em;">{{ miembro.nombre }}</div>
          <div style="color:#7f8c8d; font-weight:bold;">{{ miembro.area }}</div>
          <div style="font-size:0.85em; margin-bottom: 5px;">{{ miembro.carrera }}</div>
          <a href="mailto:{{ miembro.correo }}" style="font-size:0.8em; color:#2980b9;">{{ miembro.correo }}</a>
        </div>
      </div>
      <div class="card-back">
        <div class="scroll-content">
          <strong style="color:#7f8c8d;">Trayectoria:</strong><br>
          {{ miembro.descripcion | default: "Egresado del grupo GIDA, aportando actualmente desde la industria o la academia al sector espacial." }}
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // --- ESTRELLAS ---
    const canvas = document.getElementById('canvas-estrellas');
    const ctx = canvas.getContext('2d');
    const header = document.querySelector('.page__hero--overlay') || document.querySelector('header');
    const container = document.getElementById('mi-header-espacial');

    if (header && container) {
      header.appendChild(container);
      function resize() { canvas.width = header.offsetWidth; canvas.height = header.offsetHeight; }
      let stars = Array.from({length: 120}, () => ({
        x: Math.random() * window.innerWidth, y: Math.random() * 400, r: Math.random() * 1.5, v: Math.random() * 0.4
      }));
      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height); ctx.fillStyle = "white";
        stars.forEach(s => {
          ctx.beginPath(); ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2); ctx.fill();
          s.y += s.v; if (s.y > canvas.height) s.y = 0;
        });
        requestAnimationFrame(animate);
      }
      window.addEventListener('resize', resize); resize(); animate();
    }
  });
</script>