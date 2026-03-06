---
layout: single
title: "Recuerdos GIDA"
permalink: /recuerdos/
author_profile: true
header:
  overlay_color: "#2c3e50"
  caption: "Galeria conmemorativa del GIDA"
---

<style>
  /* Contenedor del Collage */
  .collage-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    grid-auto-rows: 150px;
    gap: 15px;
    padding: 20px;
    background: #f4f4f4;
    border-radius: 10px;
  }

  /* Estilo de cada imagen */
  .collage-item {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
    animation: float 6s ease-in-out infinite;
  }

  /* Animación de flotación aleatoria */
  @keyframes float {
    0% { transform: translate(0, 0) rotate(0deg); }
    33% { transform: translate(2px, -5px) rotate(1deg); }
    66% { transform: translate(-2px, 5px) rotate(-1deg); }
    100% { transform: translate(0, 0) rotate(0deg); }
  }

  /* Variaciones de tiempo para que no se muevan todas al mismo tiempo */
  .collage-item:nth-child(odd) { animation-duration: 7s; animation-delay: 1s; }
  .collage-item:nth-child(3n) { animation-duration: 5s; animation-delay: 0.5s; }
  .collage-item:hover {
    transform: scale(1.1) rotate(0deg) !important;
    z-index: 10;
    cursor: pointer;
  }
</style>

Esta sección rinde homenaje a nuestra trayectoria. Las imágenes se entrelazan y fluyen con suavidad, dando nueva vida a los recuerdos que nos acompañan desde hace más de trece años. Son la expresión de sueños compartidos, proyectos que nos enseñaron tanto en los aciertos como en los tropiezos, y amistades que nacieron y crecieron en el grupo. Reflejan también los intereses comunes que nos unieron, sin importar los caminos que cada uno eligiera después.

<div class="collage-container" id="collage">
  {% for file in site.static_files %}
    {% if file.path contains 'assets/images/recuerdos' %}
      <img src="{{ file.path | relative_url }}" class="collage-item" alt="Recuerdo GIDA">
    {% endif %}
  {% endfor %}
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    const container = document.getElementById('collage');
    const items = Array.from(container.children);
    
    // Algoritmo de barajado (Fisher-Yates)
    for (let i = items.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [items[i], items[j]] = [items[j], items[i]];
    }
    
    // Reinsertar en el contenedor en el nuevo orden
    items.forEach(item => container.appendChild(item));
  });
</script>
