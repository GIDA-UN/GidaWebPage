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
  /* 1. CONFIGURACIÓN DEL HEADER (Estrellas) */
  .page__hero--overlay { 
    position: relative !important; 
    background-color: #05070a !important; 
    overflow: hidden; 
  }

  .seccion-titulo { 
    border-bottom: 3px solid #950001; 
    margin: 60px 0 40px; 
    color: #1a252f; 
    font-size: 2em; 
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  
  /* 2. GRID DE TRABAJO */
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); 
    gap: 40px; /* Espaciado amplio para tarjetas grandes */
    perspective: 1500px; 
  }

  /* 3. AJUSTE VERTICAL MAESTRO (520px) */
  .member-card-container {
    width: 100%;
    height: 520px; /* Altura máxima para un look estilizado */
    cursor: pointer;
  }

  .member-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275); /* Efecto elástico al girar */
    transform-style: preserve-3d;
    box-shadow: 0 15px 35px rgba(0,0,0,0.1);
    border-radius: 20px;
  }

  .member-card-container.is-flipped .member-card-inner {
    transform: rotateY(180deg);
  }

  .card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 20px;
    background: #ffffff;
    border: 1px solid #f0f0f0;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }

  /* 4. FRONT: IMAGEN Y TEXTO */
  .member-img { 
    width: 100%; 
    height: 320px; /* Foto más grande y dominante */
    object-fit: cover;
    border-bottom: 4px solid #950001;
  }

  .info-front { 
    padding: 25px; 
    flex-grow: 1; 
    display: flex; 
    flex-direction: column; 
    justify-content: space-evenly; /* Distribuye el texto armoniosamente */
    background: linear-gradient(to bottom, #ffffff, #f9f9f9);
  }

  .info-front div:first-child { 
    font-size: 1.3em; 
    color: #2c3e50;
    line-height: 1.2;
  }

  /* 5. BACK: BIOGRAFÍA Y SCROLL */
  .card-back {
    transform: rotateY(180deg);
    background: #1a1a1a; /* Fondo oscuro elegante para la parte de atrás */
    color: #eeeeee;
    padding: 30px;
    text-align: left;
    border: 2px solid #950001;
  }

  .scroll-content {
    overflow-y: auto;
    height: 100%;
    font-size: 1em;
    line-height: 1.7;
    padding-right: 10px;
  }

  /* Scrollbar estético */
  .scroll-content::-webkit-scrollbar { width: 6px; }
  .scroll-content::-webkit-scrollbar-track { background: #333; }
  .scroll-content::-webkit-scrollbar-thumb { background: #950001; border-radius: 10px; }

  .back-title {
    color: #950001;
    font-weight: bold;
    font-size: 1.1em;
    margin-bottom: 15px;
    display: block;
    border-bottom: 1px solid #444;
    padding-bottom: 5px;
  }
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