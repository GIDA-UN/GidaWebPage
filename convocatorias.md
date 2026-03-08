---
# BLOQUE 1: CONFIGURACIÓN (Front Matter)
layout: single
title: "Convocatorias GIDA"
permalink: /convocatorias/
author_profile: true
header:
  overlay_color: "#05070a" 
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* BLOQUE 3: AJUSTES DEL TEMA Y ESTILOS */
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }
  
  .convocatorias-wrapper { margin-top: 30px; position: relative; z-index: 1; }

  .card-gida {
    background: #ffffff;
    border-radius: 15px;
    padding: 30px;
    margin-bottom: 35px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    border-left: 10px solid #950001; /* Rojo Institucional */
    transition: 0.3s;
  }

  .card-gida:hover { transform: translateY(-5px); }

  .status-badge {
    display: inline-block;
    padding: 5px 15px;
    border-radius: 20px;
    font-size: 0.8em;
    font-weight: bold;
    text-transform: uppercase;
    margin-bottom: 15px;
    background: #950001;
    color: white;
  }

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
---
# BLOQUE 1: CONFIGURACIÓN
layout: single
title: "Convocatorias GIDA"
permalink: /convocatorias/
author_profile: true
header:
  overlay_color: "#05070a" 
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* BLOQUE 3: ESTILOS VISUALES */
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }
  
  .convocatorias-wrapper { margin-top: 30px; position: relative; z-index: 1; }

  /* Estilos de los recuadros de estado (Badges) */
  .status-badge {
    display: inline-block;
    padding: 5px 15px;
    border-radius: 20px;
    font-size: 0.8em;
    font-weight: bold;
    text-transform: uppercase;
    margin-bottom: 15px;
  }
  .badge-verde { background-color: #27ae60; color: white; } /* Abierta con Link */
  .badge-amarillo { background-color: #f1c40f; color: #333; } /* Abierta sin Link */
  .badge-rojo { background-color: #950001; color: white; } /* Cerrada */

  .card-gida {
    background: #ffffff;
    border-radius: 15px;
    padding: 30px;
    margin-bottom: 35px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    border-left: 10px solid #950001;
    transition: 0.3s;
  }

  .card-gida:hover { transform: translateY(-5px); }

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
  {% if site.data.convocatorias %}
    {% for conv in site.data.convocatorias %}
      
      {% assign estado_min = conv.estado | downcase %}
      
      {% assign tiene_link = false %}
      {% if conv.link_inscripcion and conv.link_inscripcion != "" and conv.link_inscripcion != "#" %}
        {% assign tiene_link = true %}
      {% endif %}

      <div class="card-gida">
        
        {% if estado_min contains 'abierta' %}
          {% if tiene_link %}
            <div class="status-badge badge-verde">{{ conv.estado }}</div>
          {% else %}
            <div class="status-badge badge-amarillo">{{ conv.estado }}</div>
          {% endif %}
        {% else %}
          <div class="status-badge badge-rojo">{{ conv.estado }}</div>
        {% endif %}

        <h2 style="margin: 0 0 10px 0; border: none; color: #333;">{{ conv.titulo }}</h2>
        <p style="color: #950001; font-weight: bold;">📅 Cierre: {{ conv.fecha_cierre }}</p>
        <div style="line-height: 1.6; color: #444;">{{ conv.descripcion }}</div>
        
        {% if estado_min contains 'abierta' %}
          {% if tiene_link %}
            <a href="{{ conv.link_inscripcion }}" class="btn-gida" target="_blank">Postularme ahora</a>
          {% else %}
            <p style="color: #d35400; font-weight: bold; background: #fff3e0; padding: 10px; border-radius: 5px; display: inline-block; margin-top: 15px;">
              ⚠️ No hay link disponible todavía
            </p>
          {% endif %}
        {% else %}
          <p style="margin-top: 15px; color: #888; font-style: italic;">🚫 Esta convocatoria ya ha finalizado.</p>
        {% endif %}
      </div>
    {% endfor %}
  {% else %}
    <p>No hay convocatorias vigentes en este momento.</p>
  {% endif %}
</div>

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
          ctx.beginPath();
          ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
          ctx.fill();
          s.y += s.v;
          if (s.y > canvas.height) s.y = 0;
        });
        requestAnimationFrame(animate);
      }

      window.addEventListener('resize', resize);
      resize();
      animate();
    }
  });
</script>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    const canvas = document.getElementById('canvas-estrellas');
    const ctx = canvas.getContext('2d');
    // Buscamos el header del tema Minimal Mistakes para meter el canvas dentro
    const header = document.querySelector('.page__hero--overlay') || document.querySelector('header');
    const container = document.getElementById('mi-header-espacial');

    if (header && container) {
      header.appendChild(container);
      
      function resize() {
        canvas.width = header.offsetWidth;
        canvas.height = header.offsetHeight;
      }

      // Creamos las estrellas (Lógica idéntica a tus archivos profesores.md y miembros.md)
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
          ctx.beginPath();
          ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
          ctx.fill();
          s.y += s.v; // Movimiento descendente suave
          if (s.y > canvas.height) s.y = 0;
        });
        requestAnimationFrame(animate);
      }

      window.addEventListener('resize', resize);
      resize();
      animate();
    }
  });
</script>