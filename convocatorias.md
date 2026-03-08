---
layout: single
title: "Convocatorias GIDA"
permalink: /convocatorias/
header:
  overlay_color: "#05070a"
  overlay_filter: 0.5
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 400px; z-index: 0; pointer-events: none; overflow: hidden;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* Ajuste para que el hero permita ver las estrellas */
  .page__hero--overlay { 
    position: relative !important; 
    background-color: #05070a !important; 
    overflow: hidden; 
    min-height: 400px;
  }

  .convocatorias-wrapper {
    position: relative;
    z-index: 1;
    margin-top: 30px;
  }

  .card-gida {
    border-radius: 15px;
    padding: 30px;
    margin-bottom: 40px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    background: #ffffff;
    border-left: 10px solid #7f8c8d;
    transition: transform 0.3s ease;
  }

  .card-gida:hover {
    transform: translateY(-5px);
  }

  .card-abierta {
    border-left-color: #950001 !important; /* Rojo Institucional */
  }

  .status-badge {
    display: inline-block;
    padding: 6px 18px;
    border-radius: 20px;
    font-size: 0.8em;
    font-weight: bold;
    text-transform: uppercase;
    margin-bottom: 15px;
  }

  .badge-abierta { background: #950001; color: #fff; }
  .badge-cerrada { background: #eee; color: #666; }

  .btn-gida {
    background: #950001;
    color: white !important;
    padding: 12px 25px;
    border-radius: 8px;
    text-decoration: none;
    display: inline-block;
    font-weight: bold;
    margin-top: 15px;
  }
</style>

<div class="convocatorias-wrapper">
  <p style="text-align: center; color: #666; font-size: 1.1em; margin-bottom: 40px;">
    Únete a nuestros proyectos de investigación y lleva tu potencial al espacio.
  </p>

  {% if site.data.convocatorias %}
    {% for conv in site.data.convocatorias %}
      <div class="card-gida {% if conv.estado contains 'Abierta' %}card-abierta{% endif %}">
        <div class="status-badge {% if conv.estado contains 'Abierta' %}badge-abierta{% else %}badge-cerrada{% endif %}">
          {{ conv.estado }}
        </div>

        <h2 style="margin: 0 0 10px 0; color: #333; border: none;">{{ conv.titulo }}</h2>
        
        <p style="color: #950001; font-weight: bold;">
          📅 Cierre de inscripciones: {{ conv.fecha_cierre }}
        </p>

        <div style="line-height: 1.8; color: #444;">
          {{ conv.descripcion }}
        </div>

        {% if conv.estado contains 'Abierta' %}
          <a href="{{ conv.link_inscripcion }}" class="btn-gida" target="_blank">Postularme</a>
        {% else %}
          <p style="margin-top: 20px; color: #888; font-style: italic;">🚫 Convocatoria cerrada</p>
        {% endif %}
      </div>
    {% endfor %}
  {% else %}
    <p>No hay convocatorias registradas actualmente.</p>
  {% endif %}
</div>

<script>
  const canvas = document.getElementById('canvas-estrellas');
  const ctx = canvas.getContext('2d');
  let w, h, stars = [];

  function init() {
    w = canvas.width = window.innerWidth;
    h = canvas.height = 400; // Altura del header
    stars = [];
    for (let i = 0; i < 150; i++) {
      stars.push({
        x: Math.random() * w,
        y: Math.random() * h,
        size: Math.random() * 2,
        speed: Math.random() * 0.5
      });
    }
  }

  function draw() {
    ctx.clearRect(0, 0, w, h);
    ctx.fillStyle = '#fff';
    stars.forEach(s => {
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.size, 0, Math.PI * 2);
      ctx.fill();
      s.y -= s.speed;
      if (s.y < 0) s.y = h;
    });
    requestAnimationFrame(draw);
  }

  window.addEventListener('resize', init);
  init();
  draw();
</script>