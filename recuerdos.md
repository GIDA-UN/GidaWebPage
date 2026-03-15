---
layout: single
title: "Recuerdos GIDA"
permalink: /recuerdos/
author_profile: true
header:
  overlay_color: "#05070a"
  caption: "Galeria conmemorativa del GIDA"
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* 1. AJUSTES DEL HEADER (Estrellas) */
  header.page__hero--overlay, .page__hero--overlay {
    position: relative !important;
    background-color: #05070a !important;
    overflow: hidden;
  }

  .page__hero-content, .wrapper {
    position: relative;
    z-index: 5;
  }

  /* 2. COLLAGE TIPO MOSAICO (Masonry) */
  .collage-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    grid-auto-rows: 180px; 
    grid-auto-flow: dense; 
    gap: 12px;
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
    transition: transform 0.3s ease, filter 0.3s ease;
    animation: float 6s ease-in-out infinite;
  }

  .collage-item:nth-child(5n) { grid-column: span 2; grid-row: span 2; }
  .collage-item:nth-child(7n) { grid-column: span 2; }
  .collage-item:nth-child(3n) { grid-row: span 2; }

  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    33% { transform: translate(2px, -5px) rotate(0.5deg); }
    66% { transform: translate(-2px, 5px) rotate(-0.5deg); }
    100% { transform: translate(0, 0) rotate(0deg); }
  }

  .collage-item:hover { 
    transform: scale(1.05); 
    z-index: 10; 
    cursor: pointer; 
    filter: brightness(1.1); 
  }

  /* 3. ESTILOS DEL VISOR (LIGHTBOX) */
  .lightbox-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0, 0, 0, 0.9);
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    cursor: zoom-out;
  }

  .lightbox-overlay img {
    max-width: 90%;
    max-height: 85%;
    border-radius: 5px;
    box-shadow: 0 0 30px rgba(0,0,0,0.5);
    transform: scale(0.9);
    transition: transform 0.3s ease;
  }

  .lightbox-overlay.active { display: flex; }
  .lightbox-overlay.active img { transform: scale(1); }

  .close-lightbox {
    position: absolute;
    top: 20px; right: 30px;
    color: white;
    font-size: 50px;
    font-weight: 300;
    cursor: pointer;
    line-height: 1;
  }
</style>

Esta sección rinde homenaje a nuestra trayectoria. Las imágenes fluyen en un mosaico dinámico.

<div class="collage-container" id="collage">
  {% assign count = 0 %}
  {% for file in site.static_files %}
    {% if file.path contains 'assets/images/recuerdos' %}
      {% if count < 100 %}
        <img src="{{ file.path | relative_url }}" 
             class="collage-item" 
             alt="Recuerdo GIDA" 
             loading="lazy"> 
        {% assign count = count | plus: 1 %}
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

<div id="lightbox" class="lightbox-overlay" onclick="this.classList.remove('active')">
  <span class="close-lightbox">&times;</span>
  <img id="lightbox-img" src="" alt="Zoom Recuerdo">
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // 1. REFERENCIAS
    const collageContainer = document.getElementById('collage');
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightbox-img');

    // 2. LÓGICA DEL VISOR (Dentro del DOMContentLoaded)
    collageContainer.addEventListener('click', function(e) {
      if (e.target.classList.contains('collage-item')) {
        lightboxImg.src = e.target.src;
        lightbox.classList.add('active');
      }
    });

    // 3. ESTRELLAS
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

    // 4. BARAJADO (Shuffle)
    const items = Array.from(collageContainer.children);
    for (let i = items.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [items[i], items[j]] = [items[j], items[i]];
    }
    items.forEach(item => collageContainer.appendChild(item));
  });
</script>