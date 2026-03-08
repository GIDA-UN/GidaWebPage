---
# ==========================================
# BLOQUE 1: CONFIGURACIÓN DE PÁGINA
# ==========================================
layout: single
title: "Dirección Académica"
permalink: /profesores/
author_profile: true
header:
  overlay_color: "#05070a"
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* BLOQUE 3: ESTILOS DE PERFIL PROFESIONAL (CSS) */
  /* ZONA DE CAMBIO: Colores institucionales y sombras */
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }

  .profesor-container {
    max-width: 900px;
    margin: 40px auto;
    background: #fff;
    border-radius: 15px;
    display: flex; /* Diseño horizontal para más info */
    overflow: hidden;
    box-shadow: 0 15px 35px rgba(0,0,0,0.2);
    border-left: 8px solid #950001; /* Franja Roja UNAL */
  }

  .profesor-left {
    background: #f8f9fa;
    padding: 40px;
    text-align: center;
    flex: 1;
  }

  .profesor-right {
    padding: 40px;
    flex: 2;
  }

  .profesor-img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    border: 5px solid #fff;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }

  .tag-area {
    display: inline-block;
    background: #950001;
    color: white;
    padding: 5px 15px;
    border-radius: 20px;
    font-size: 0.8em;
    font-weight: bold;
    margin-bottom: 10px;
  }

  .lineas-investigacion {
    list-style: none;
    padding: 0;
    margin-top: 15px;
  }

  .lineas-investigacion li {
    padding: 5px 0;
    border-bottom: 1px solid #eee;
    font-size: 0.9em;
  }
</style>

<div class="profesor-container">
  {% assign docentes = site.data.miembros | where: "tipo", "profesor" %}
  {% for profe in docentes %}
  <div class="profesor-left">
    <img src="{{ profe.foto | relative_url }}" class="profesor-img" alt="{{ profe.nombre }}">
    <h2 style="margin: 15px 0 5px;">{{ profe.nombre }}</h2>
    <div class="tag-area">PROFESOR ASOCIADO</div>
    <p style="font-size: 0.9em; color: #666;">{{ profe.correo }}</p>
    <a href="https://cvlac.minciencias.gov.co" class="btn btn--primary" target="_blank">Ver CvLAC</a>
  </div>

  <div class="profesor-right">
    <h3 style="color: #950001; margin-top: 0;">Perfil Académico</h3>
    <p style="line-height: 1.6; font-size: 0.95em; text-align: justify;">
      {{ profe.descripcion }} </p>

    <h4 style="margin-bottom: 10px;">Formación Destacada</h4>
    <ul class="lineas-investigacion">
      <li><strong>Doctor of Philosophy (Ph.D.):</strong> University of Leicester, UK</li>
      <li><strong>MSc in Control Systems:</strong> University of Sheffield, UK</li>
      <li><strong>Ingeniería Mecánica:</strong> Universidad Nacional de Colombia</li>
    </ul>

    <h4 style="margin-top: 20px; margin-bottom: 10px;">Líneas de Investigación</h4>
    <div style="display: flex; flex-wrap: wrap; gap: 10px;">
      <span style="background: #eee; padding: 5px 10px; border-radius: 5px; font-size: 0.85em;">Control Robusto</span>
      <span style="background: #eee; padding: 5px 10px; border-radius: 5px; font-size: 0.85em;">Sistemas No Lineales</span>
      <span style="background: #eee; padding: 5px 10px; border-radius: 5px; font-size: 0.85em;">Robótica Móvil</span>
    </div>
  </div>
  {% endfor %}
</div>

<script>
  /* [Mismo script de animación de estrellas que ya tienes] */
</script>