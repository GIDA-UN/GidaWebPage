---
layout: single
title: "Recuerdos GIDA"
permalink: /recuerdos/
author_profile: true
header:
  overlay_color: "#05070a" # Color base oscuro para el espacio
  caption: "Galeria conmemorativa del GIDA"
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* 2. AJUSTES DEL HEADER DEL TEMA */
  header.page__hero--overlay, .page__hero--overlay {
    position: relative !important;
    background-color: #05070a !important; /* Fondo negro espacial */
    overflow: hidden;
  }

  .page__hero-content, .wrapper {
    position: relative;
    z-index: 5; /* Asegura que el título esté sobre las estrellas */
  }

  /* 3. ESTILOS DE TU COLLAGE (Mantenemos tu diseño original) */
  .collage-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    grid-auto-rows: 150px;
    gap: 15px;
    padding: 20px;
    background: #f4f4f4;
    border-radius: 10px;
    margin-top: 30px;
  }

  .collage-item {
    width: 100%; height: 100%;
    object-fit: cover;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
    animation: float 6s ease-in-out infinite;
  }

  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    33% { transform: translate(2px, -5px) rotate(1deg); }
    66% { transform: translate(-2px, 5px) rotate(-1deg); }
    100% { transform: translate(0, 0) rotate(0deg); }
  }

  .collage-item:nth-child(odd) { animation-duration: 7s; }
  .collage-item:hover { transform: scale(1.1); z-index: 10; cursor: pointer; }
</style>

Esta sección rinde homenaje a nuestra trayectoria. Las imágenes se entrelazan y fluyen con suavidad.

<div class="collage-container" id="collage">
  {% for file in site.static_files %}
    {% if file.path contains 'assets/images/recuerdos' %}
      <img src="{{ file.path | relative_url }}" class="collage-item" alt="Recuerdo GIDA">
    {% endif %}
  {% endfor %}
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // --- LÓGICA DE ESTRELLAS ---
    const canvas = document.getElementById('canvas-estrellas');
    const ctx = canvas.getContext('2d');
    const header = document.querySelector('.page__hero--overlay') || document.querySelector('header');
    const container = document.getElementById('mi-header-espacial');

    if (header && container) {
      header.appendChild(container); // Metemos el canvas dentro de la cinta del header
      
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

    // --- LÓGICA DE BARAJADO DEL COLLAGE ---
    const collageContainer = document.getElementById('collage');
    const items = Array.from(collageContainer.children);
    for (let i = items.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [items[i], items[j]] = [items[j], items[i]];
    }
    items.forEach(item => collageContainer.appendChild(item));
  });
</script>