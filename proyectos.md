---
layout: single
title: "Proyectos e Investigación"
permalink: /proyectos/
author_profile: true
header:
  overlay_color: "#05070a"
---

<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* Ajustes base para el header animado */
  .page__hero--overlay { position: relative !important; background-color: #05070a !important; overflow: hidden; }

  /* Estilos para el contenido de Proyectos */
  .proyectos-intro {
    font-size: 1.15em;
    line-height: 1.8;
    color: #333;
    text-align: justify;
    margin-bottom: 50px;
  }

  .seccion-lideres {
    border-bottom: 2px solid #950001;
    margin: 40px 0 30px;
    color: #2c3e50;
    font-size: 1.8em;
    font-weight: bold;
  }

  /* Grid de Líderes */
  .lideres-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin-top: 20px;
  }

  .lider-card {
    background: #fdfdfd;
    border: 1px solid #e1e1e1;
    border-left: 5px solid #950001;
    padding: 20px;
    border-radius: 8px;
    transition: 0.3s;
  }

  .lider-card:hover {
    transform: translateX(10px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.08);
  }

  .lider-nombre {
    font-weight: bold;
    font-size: 1.2em;
    color: #2c3e50;
    display: block;
  }

  .lider-proyecto {
    color: #950001;
    font-weight: 600;
    font-size: 0.9em;
    text-transform: uppercase;
    margin-bottom: 10px;
    display: block;
  }

  .lider-correo {
    font-size: 0.9em;
    color: #2980b9;
    text-decoration: none;
  }
  
  .lider-correo:hover { text-decoration: underline; }
</style>

<div class="proyectos-intro">
  Actualmente, el <strong>Grupo de Investigación y Desarrollo Aeroespacial (GIDA)</strong> desarrolla sus actividades en torno a tres líneas principales de trabajo. 
  <br><br>
  En primer lugar, se encuentra la <strong>construcción de una nueva base de pruebas</strong>, orientada a fortalecer las capacidades experimentales del grupo y permitir la validación de sistemas en condiciones controladas. 
  <br><br>
  De manera paralela, se continúa con el avance en el <strong>desarrollo de un cohete experimental</strong>, haciendo énfasis en el análisis e integración de sistemas periféricos como instrumentación, telemetría y control, fundamentales para su operación. 
  <br><br>
  Finalmente, el grupo mantiene el desarrollo de <strong>proyectos en ambientes análogos</strong>, particularmente en sistemas de cultivos (SpaceCrops), con el objetivo de investigar soluciones sostenibles aplicables tanto en contextos espaciales como terrestres.
</div>

<h2 class="seccion-lideres">Líderes de Proyecto</h2>

<div class="lideres-grid">
  
  <div class="lider-card">
    <span class="lider-proyecto">Cohetería Experimental & Base de Pruebas</span>
    <span class="lider-nombre">Jesus Andres Acosta Varela</span>
    <a href="mailto:jaacostav@unal.edu.co" class="lider-correo">jaacostav@unal.edu.co</a>
  </div>

  <div class="lider-card">
    <span class="lider-proyecto">SpaceCrops (Ambientes Análogos)</span>
    <span class="lider-nombre">Paola Alejandra Bello Buitrago</span>
    <a href="mailto:pabellob@unal.edu.co" class="lider-correo">pabellob@unal.edu.co</a>
  </div>

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

      let stars = Array.from({length: 150}, () => ({
        x: Math.random() * window.innerWidth, 
        y: Math.random() * 400, 
        r: Math.random() * 1.5, 
        v: Math.random() * 0.5 
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