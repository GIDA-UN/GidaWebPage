---
# ==========================================
# BLOQUE 1: CONFIGURACIÓN DE PÁGINA
# ==========================================
layout: single
title: "Dirección Académica"
permalink: /profesores/
author_profile: true
header:
  overlay_color: "#05070a" # Fondo negro de respaldo
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* BLOQUE 3: ESTILOS VISUALES */
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }

  .profesor-card {
    max-width: 950px;
    margin: 40px auto;
    background: #fff;
    border-radius: 15px;
    display: flex;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    border-left: 10px solid #950001; /* Rojo Institucional */
  }

  .profesor-sidebar { background: #fdfdfd; padding: 40px; text-align: center; flex: 1; border-right: 1px solid #eee; }
  .profesor-main { padding: 40px; flex: 2; }
  .profesor-photo { width: 180px; height: 180px; border-radius: 50%; object-fit: cover; border: 4px solid #fff; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
  
  .tag-is { background: #950001; color: #fff; padding: 4px 12px; border-radius: 20px; font-size: 0.75em; font-weight: bold; text-transform: uppercase; }
  .estudios-lista { list-style: none; padding: 0; font-size: 0.9em; }
  .estudios-lista li { margin-bottom: 15px; position: relative; padding-left: 25px; }
  .estudios-lista li::before { content: "🎓"; position: absolute; left: 0; }
</style>

{% for profe in site.data.profesores %}
<div class="profesor-card">
  <div class="profesor-sidebar">
    <img src="{{ profe.foto | relative_url }}" class="profesor-photo" alt="{{ profe.nombre }}">
    <h2 style="margin: 15px 0 5px;">{{ profe.nombre }}</h2>
    <span class="tag-is">{{ profe.cargo }}</span>
    <p style="margin-top: 15px; font-size: 0.9em; color: #333;">
      <a href="mailto:{{ profe.correo }}" style="color: #2980b9; text-decoration: none;">{{ profe.correo }}</a>
    </p>
  </div>

  <div class="profesor-main">
    <h3 style="color: #950001; margin-top: 0;">Perfil Profesional</h3>
    <p style="text-align: justify; line-height: 1.6;">{{ profe.perfil }}</p>
    
    <h4 style="border-bottom: 1px solid #eee; padding-bottom: 5px;">Formación Académica</h4>
    <ul class="estudios-lista">
      {% for estudio in profe.estudios %}
      <li>
        <strong>{{ estudio.grado }}</strong><br>
        <span style="color: #666;">{{ estudio.institucion }}</span><br>
        {% if estudio.tesis %}
          <small style="font-style: italic; color: #888;">Tesis: {{ estudio.tesis }}</small>
        {% endif %}
      </li>
      {% endfor %}
    </ul>
  </div>
</div>
{% endfor %}

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