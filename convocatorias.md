---
layout: single
title: "Convocatorias GIDA"
permalink: /convocatorias/
header:
  overlay_color: "#05070a"
  overlay_filter: 0.5
  overlay_image: /assets/images/header-stars.jpg # Asegúrate de tener una imagen de fondo oscuro aquí
  caption: "Explora nuevas fronteras con GIDA"
---

<style>
  /* Contenedor principal */
  .convocatorias-wrapper {
    margin-top: 20px;
  }

  /* Tarjeta de convocatoria */
  .card-gida {
    border-radius: 12px;
    padding: 25px;
    margin-bottom: 30px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    background: #ffffff;
    transition: transform 0.3s ease;
    border-left: 10px solid #7f8c8d; /* Gris por defecto */
    position: relative;
    overflow: hidden;
  }

  .card-gida:hover {
    transform: translateY(-5px);
  }

  /* Estado Abierta */
  .card-abierta {
    border-left-color: #27ae60 !important;
  }

  /* Badge de Estado */
  .status-badge {
    display: inline-block;
    padding: 5px 15px;
    border-radius: 50px;
    font-size: 0.75em;
    font-weight: 800;
    text-transform: uppercase;
    margin-bottom: 15px;
  }

  .badge-abierta { background: #e8f5e9; color: #2e7d32; }
  .badge-cerrada { background: #f5f5f5; color: #616161; }

  /* Botón de acción */
  .btn-gida {
    background: #950001;
    color: white !important;
    padding: 12px 25px;
    border-radius: 8px;
    text-decoration: none;
    display: inline-block;
    font-weight: bold;
    margin-top: 15px;
    transition: background 0.3s;
  }

  .btn-gida:hover {
    background: #7a0000;
  }
</style>

Aquí encontrarás las oportunidades vigentes para integrarte a nuestros equipos de investigación y desarrollo.

<div class="convocatorias-wrapper">
{% if site.data.convocatorias %}
  {% for conv in site.data.convocatorias %}
    <div class="card-gida {% if conv.estado contains 'Abierta' %}card-abierta{% endif %}">
      
      <div class="status-badge {% if conv.estado contains 'Abierta' %}badge-abierta{% else %}badge-cerrada{% endif %}">
        {{ conv.estado }}
      </div>

      <h2 style="margin: 0 0 10px 0; color: #333; border-bottom: none;">{{ conv.titulo }}</h2>
      
      <p style="color: #666; font-size: 0.9em; margin-bottom: 15px;">
        <strong>📅 Cierre:</strong> {{ conv.fecha_cierre }}
      </p>

      <div style="color: #444; line-height: 1.6;">
        {{ conv.descripcion }}
      </div>

      {% if conv.estado contains 'Abierta' %}
        <a href="{{ conv.link_inscripcion }}" class="btn-gida" target="_blank">
          Postularme ahora
        </a>
      {% else %}
        <p style="margin-top: 20px; color: #999; font-style: italic;">
          🚫 Esta convocatoria ha finalizado.
        </p>
      {% endif %}
    </div>
  {% endfor %}
{% else %}
  <div class="notice--info">
    <p>Estamos actualizando la base de datos. Por favor, regresa pronto para ver nuevas vacantes.</p>
  </div>
{% endif %}
</div>