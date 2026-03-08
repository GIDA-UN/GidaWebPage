---
layout: single
title: "Convocatorias GIDA"
permalink: /convocatorias/
header:
  overlay_color: "#05070a"
---

<style>
  .convocatoria-card {
    border-radius: 10px;
    padding: 20px;
    margin: 20px 0;
    border-left: 8px solid #7f8c8d;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    background: #ffffff;
  }
  .estado-abierta { border-left-color: #27ae60 !important; }
  .estado-cerrada { border-left-color: #7f8c8d !important; opacity: 0.8; }
  .btn-gida {
    background: #950001;
    color: white !important;
    padding: 10px 20px;
    border-radius: 5px;
    text-decoration: none;
    display: inline-block;
    font-weight: bold;
  }
</style>

Aquí encontrarás las oportunidades para unirte a nuestros proyectos.

{% if site.data.convocatorias %}
  {% for conv in site.data.convocatorias %}
    <div class="convocatoria-card {% if conv.estado == 'Abierta' %}estado-abierta{% else %}estado-cerrada{% endif %}">
      <h3 style="margin-top: 0;">{{ conv.titulo }}</h3>
      <p><strong>Estado:</strong> {{ conv.estado }} | <strong>Cierre:</strong> {{ conv.fecha_cierre }}</p>
      <p>{{ conv.descripcion }}</p>
      
      {% if conv.estado == 'Abierta' %}
        <a href="{{ conv.link_inscripcion }}" class="btn-gida" target="_blank">Postularme</a>
      {% else %}
        <span style="color: #888; font-style: italic;">🚫 Convocatoria finalizada</span>
      {% endif %}
    </div>
  {% endfor %}
{% else %}
  <p>No hay convocatorias registradas en el sistema.</p>
{% endif %}