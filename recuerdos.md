---
layout: single
title: "Recuerdos GIDA"
permalink: /recuerdos/
author_profile: true
header:
  # 'transparent' permite que el canvas de estrellas se vea detrás del título
  overlay_color: "transparent"
  caption: "Galería conmemorativa del GIDA"
---

<div id="starfield-container" style="position: absolute; top: 0; left: 0; width: 100%; height: 450px; z-index: -1; overflow: hidden; background: #05070a;">
  <canvas id="starfield"></canvas>
</div>

<style>
  /* CONFIGURACIÓN DEL HEADER */
  .page__hero--overlay {
    background-color: transparent !important; /* Quita el color sólido por defecto del tema */
    position: relative;
    height: 450px; /* Altura total de la sección de estrellas */
    display: flex;
    align-items: center; /* Centra el título verticalmente */
  }

  /* ESTILOS DEL COLLAGE DE FOTOS */
  .collage-container {
    display: grid; /* Sistema de rejilla moderno */
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Columnas responsivas */
    grid-auto-rows: 150px; /* Altura fija para mantener simetría */
    gap: 15px; /* Espacio entre fotos */
    padding: 20px;
    background: #f4f4f4; /* Fondo claro para que resalten las fotos */
    border-radius: 10px;
    margin-top: 20px;
  }

  .collage-item {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Recorta la imagen para que llene el cuadro sin deformarse */
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease; /* Suavidad al pasar el mouse */
    animation: float 6s ease-in-out infinite; /* Llama a la animación de flotación */
  }

  /* ANIMACIÓN DE FLOTACIÓN (EFECTO CERO GRAVEDAD) */
  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    33% { transform: translate(2px, -5px) rotate(1deg); }
    66% { transform: translate(-2px, 5px) rotate(-1deg); }
    100% { transform: translate(0, 0) rotate(0deg); }
  }

  /* EFECTO HOVER (CUANDO PASAS EL MOUSE) */
  .collage-item:hover {
    transform: scale(1.1) rotate(0deg) !important; /* La foto se agranda */
    z-index: 10;
    cursor: pointer;
  }
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
  // --- MOTOR DE ESTRELLAS ---
  const canvas = document.getElementById('starfield');
  const ctx = canvas.getContext('2d');
  let stars = [];

  // Ajusta el tamaño del lienzo al ancho de la pantalla
  function resize() {
    canvas.width = window.innerWidth;
    canvas.height = 450; 
  }

  // Definición de una "Estrella"
  class Star {
    constructor() {
      this.x = Math.random() * canvas.width; // Posición horizontal aleatoria
      this.y = Math.random() * canvas.height; // Posición vertical aleatoria
      this.size = Math.random() * 2; // Tamaño variado (estrellas grandes y pequeñas)
      this.speed = Math.random() * 0.3 + 0.1; // Velocidad de caída sutil
    }
    update() {
      this.y += this.speed; // Mueve la estrella hacia abajo
      if (this.y > canvas.height) { // Si sale de la pantalla, vuelve arriba
        this.y = 0;
        this.x = Math.random() * canvas.width;
      }
    }
    draw() {
      ctx.fillStyle = 'white'; // Color de la estrella
      ctx.beginPath();
      ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
      ctx.fill();
    }
  }

  // Crea el ejército de 150 estrellas
  function initStars() {
    resize();
    stars = [];
    for (let i = 0; i < 150; i++) stars.push(new Star());
  }

  // Dibuja y actualiza cuadro por cuadro (60fps)
  function animateStars() {
    ctx.clearRect(0, 0, canvas.width, canvas.height); // Borra el cuadro anterior
    stars.forEach(star => {
      star.update();
      star.draw();
    });
    requestAnimationFrame(animateStars); // Llama al siguiente cuadro
  }

  // --- EJECUCIÓN AL CARGAR LA PÁGINA ---
  document.addEventListener("DOMContentLoaded", function() {
    initStars();
    animateStars();
    window.addEventListener('resize', initStars); // Reajusta si cambian el tamaño de ventana

    // --- ALGORITMO DE BARAJADO (PARA LAS FOTOS) ---
    const container = document.getElementById('collage');
    const items = Array.from(container.children);
    
    // Intercambia posiciones aleatoriamente
    for (let i = items.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [items[i], items[j]] = [items[j], items[i]];
    }
    
    // Coloca las fotos en el nuevo orden aleatorio
    items.forEach(item => container.appendChild(item));
  });
</script>