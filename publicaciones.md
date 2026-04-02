---
layout: single
title: "Publicaciones Científicas"
permalink: /publicaciones/
author_profile: true
header:
  overlay_color: "#05070a"
---
<div id="mi-header-espacial" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none;">
  <canvas id="canvas-estrellas"></canvas>
</div>

<style>
  /* 1. AJUSTES DEL HEADER (Para que funcionen las estrellas) */
  .page__hero--overlay { 
    position: relative !important; 
    background-color: #05070a !important; 
    overflow: hidden; 
  }

  /* 2. FILTROS POR AÑO */
  .filter-container { 
    margin-bottom: 40px; 
    text-align: center; 
    position: relative;
    z-index: 10;
  }
  .filter-btn {
    background: #f4f4f4; 
    border: 1px solid #ddd; 
    padding: 8px 18px;
    margin: 5px; 
    border-radius: 20px; 
    cursor: pointer; 
    transition: 0.3s;
    font-family: inherit;
    font-weight: 500;
  }
  .filter-btn:hover { background: #e0e0e0; }
  .filter-btn.active { 
    background: #950001; 
    color: white !important; 
    border-color: #950001; 
    box-shadow: 0 4px 10px rgba(149, 0, 1, 0.3);
  }

  /* 3. GRID DE ARTÍCULOS */
  .pub-grid { 
    display: grid; 
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); 
    gap: 25px; 
  }
  
  .pub-card {
    background: #fff; 
    border-radius: 10px; 
    border: 1px solid #e1e1e1;
    display: flex; 
    flex-direction: column; 
    transition: 0.3s; 
    position: relative;
    height: 100%;
  }
  .pub-card:hover { 
    transform: translateY(-5px); 
    box-shadow: 0 10px 25px rgba(0,0,0,0.15); 
  }
  
  .pub-badge {
    position: absolute; 
    top: 15px; 
    right: 15px; 
    background: #950001;
    color: white; 
    padding: 2px 12px; 
    border-radius: 5px; 
    font-size: 0.85em; 
    font-weight: bold;
  }

  .pub-body { padding: 25px; flex-grow: 1; }
  .pub-title { 
    font-weight: bold; 
    font-size: 1.15em; 
    color: #2c3e50; 
    margin-bottom: 12px; 
    display: block; 
    line-height: 1.3; 
    padding-right: 40px; /* Espacio para el badge */
  }
  .pub-authors { 
    font-size: 0.85em; 
    color: #7f8c8d; 
    margin-bottom: 12px; 
    font-style: italic; 
  }
  .pub-excerpt { 
    font-size: 0.95em; 
    line-height: 1.6; 
    color: #444; 
    text-align: justify; 
  }

  .pub-footer { 
    background: #fdfdfd; 
    padding: 15px; 
    border-top: 1px solid #eee; 
    text-align: center; 
    border-radius: 0 0 10px 10px; 
  }
  .btn-view { 
    background: #2980b9; 
    color: white !important; 
    padding: 10px 25px; 
    border-radius: 6px; 
    text-decoration: none !important; 
    font-size: 0.95em; 
    cursor: pointer; 
    display: inline-block;
    transition: background 0.3s;
  }
  .btn-view:hover { background: #1f6391; }

  /* 4. MODAL DEL VISOR PDF (PROFESIONAL) */
  .modal-visor {
    display: none; 
    position: fixed; 
    z-index: 10000; /* Por encima de todo */
    left: 0; 
    top: 0;
    width: 100%; 
    height: 100%; 
    background-color: rgba(0,0,0,0.95);
  }
  .modal-content {
    position: relative; 
    margin: auto; 
    width: 95%; 
    height: 85vh; 
    top: 7vh;
  }
  .close-visor {
    position: absolute; 
    top: -50px; 
    right: 0; 
    color: #fff; 
    font-size: 45px;
    font-weight: 300; 
    cursor: pointer; 
    line-height: 1;
    transition: color 0.3s;
  }
  .close-visor:hover { color: #950001; }
  
  iframe { 
    width: 100%; 
    height: 100%; 
    border: none; 
    border-radius: 5px; 
    background: #333; 
  }

  /* Ajustes para móviles */
  @media (max-width: 600px) {
    .modal-content { width: 100%; height: 80vh; top: 10vh; }
    .pub-grid { grid-template-columns: 1fr; }
  }
</style>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterPubs('all', this)">Todos</button>
  <button class="filter-btn" onclick="filterPubs('2019', this)">2019</button>
  <button class="filter-btn" onclick="filterPubs('2017', this)">2017</button>
  <button class="filter-btn" onclick="filterPubs('2016', this)">2016</button>
  <button class="filter-btn" onclick="filterPubs('2015', this)">2015</button>
  <button class="filter-btn" onclick="filterPubs('2014', this)">2014</button>
</div>

<div class="pub-grid" id="pub-grid">

  <div class="pub-card" data-year="2019">
    <span class="pub-badge">2019</span>
    <div class="pub-body">
      <span class="pub-title">DISTRIBUCIÓN DE CO2 EN CASCO CONDOR</span>
      <div class="pub-authors">Camilo Zorro, Carlos Duque-Daza</div>
      <p class="pub-excerpt">Análisis mediante OpenFoam para optimizar la seguridad en actividades extravehiculares del traje Condor.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/CATE 2019 Determinación de distribución de CO2 en casco del simulador de traje espacial CONDOR.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2015">
    <span class="pub-badge">2015</span>
    <div class="pub-body">
      <span class="pub-title">MISIÓN LANZAMIENTO COHETE PROMETEO I</span>
      <div class="pub-authors">N. Álvarez, J. Huérfano, O. Ojeda</div>
      <p class="pub-excerpt">Logística y ejecución del primer lanzamiento a 3km de altura en la Universidad Nacional.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de CATE2015-DiseoMisinPrometeoI.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2015">
    <span class="pub-badge">2015</span>
    <div class="pub-body">
      <span class="pub-title">SISTEMA DE TELEMETRÍA PARA VEHÍCULOS</span>
      <div class="pub-authors">Jerson Huérfano, Oscar Ojeda, Nelson Álvarez</div>
      <p class="pub-excerpt">Diseño de una IMU capaz de soportar aceleraciones de 32g para reconstrucción de trayectorias.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de CATE2015-SistemadeTelemetra.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2016">
    <span class="pub-badge">2016</span>
    <div class="pub-body">
      <span class="pub-title">COLOMBIA AEROESPACIAL 2026</span>
      <div class="pub-authors">J. Bonilla, O. Ojeda, L. Villagrán, et al.</div>
      <p class="pub-excerpt">Plan estratégico integral para el fortalecimiento del sector aeroespacial colombiano.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de ColombiaAeroespacial2018-2026.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2015">
    <span class="pub-badge">2015</span>
    <div class="pub-body">
      <span class="pub-title">BANCO DE PRUEBAS PARA MOTORES COHETE</span>
      <div class="pub-authors">N. Álvarez, J. Huérfano, O. Ojeda</div>
      <p class="pub-excerpt">Diseño mecánico de un banco modular para caracterización de empuje hasta 1000 N.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de DISEODEUNBANCODEPRUEBASESTTICOPARAPRUEBAYCARACTERIZACINDEMOTORESCOHETE.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2017">
    <span class="pub-badge">2017</span>
    <div class="pub-body">
      <span class="pub-title">SIMULADOR ATMÓSFERA MARCIANA (SAM)</span>
      <div class="pub-authors">O. López, Y. Méndez, O. Ojeda, J. Paéz</div>
      <p class="pub-excerpt">Cámara de simulación de vacío y UV para pruebas de viabilidad biológica extremófila.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de DesarrollodeunaCmaradeSimulacindeCondicionesAtmosfricasMarcianas1.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2017">
    <span class="pub-badge">2017</span>
    <div class="pub-body">
      <span class="pub-title">HOJA DE RUTA AEROESPACIAL 2018-2026</span>
      <div class="pub-authors">Oscar Ojeda, Camilo Zorro</div>
      <p class="pub-excerpt">Estrategia nacional para subsanar el rezago aeroespacial mediante fases gubernamentales.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de HojadeRutaColombiaAeroespacial.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2016">
    <span class="pub-badge">2016</span>
    <div class="pub-body">
      <span class="pub-title">INTRODUCCIÓN A LA PARADOJA DE FERMI</span>
      <div class="pub-authors">Yael Méndez, Oscar Ojeda</div>
      <p class="pub-excerpt">Análisis astrobiológico sobre la falta de evidencia de civilizaciones tecnológicas galácticas.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de Laparadojadefermidondeestantodos.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2016">
    <span class="pub-badge">2016</span>
    <div class="pub-body">
      <span class="pub-title">GIDA-UN: TOOL FOR AEROSPACE EDUCATION</span>
      <div class="pub-authors">Oscar Ojeda, Jorge Sofrony, Juan Vargas</div>
      <p class="pub-excerpt">Análisis del modelo GIDA como herramienta pedagógica presentado en el IAC México.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de OjedaSofronyVargas.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2014">
    <span class="pub-badge">2014</span>
    <div class="pub-body">
      <span class="pub-title">MANUFACTURA DE COMBUSTIBLE CANDY</span>
      <div class="pub-authors">N. Alvarez, O. Gomez, J. Monroy, O. Ojeda</div>
      <p class="pub-excerpt">Procesos de purificación y fundición de Nitrato de Potasio y Sorbitol para motores cohete.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de ProcesodeManufacturadeGranosdeCombustibleSlidotipoCandyparaMotoresCohete-Entrega2.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2016">
    <span class="pub-badge">2016</span>
    <div class="pub-body">
      <span class="pub-title">SOUTH AMERICAN SPACE AGENCY (SASA)</span>
      <div class="pub-authors">J. Silva-Martinez, A. Aguilar, O. Ojeda, et al.</div>
      <p class="pub-excerpt">Examen de factibilidad para una agencia regional de cooperación espacial en Sudamérica.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de Study on the development of a South American Space Agency.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2017">
    <span class="pub-badge">2017</span>
    <div class="pub-body">
      <span class="pub-title">TERRESTRIAL ANALOGUES IN COLOMBIA</span>
      <div class="pub-authors">Oscar Ojeda, Monika Pardo</div>
      <p class="pub-excerpt">Identificación de sitios colombianos análogos a Marte y la Luna para pruebas de hardware.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de Terrestrial analogues to Mars the Moon and microgravity Analysis of research sites in Colombia as an emerging country in space activities.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2017">
    <span class="pub-badge">2017</span>
    <div class="pub-body">
      <span class="pub-title">HABITABILIDAD EN HÁBITATS MARCIANOS</span>
      <div class="pub-authors">C. Alvarez, J. Fernandez, O. Lopez, O. Ojeda</div>
      <p class="pub-excerpt">Propuesta arquitectónica de módulos en túneles de lava para protección contra radiación.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/Copia de conceptos de habitabilidad.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2019">
    <span class="pub-badge">2019</span>
    <div class="pub-body">
      <span class="pub-title">BANCOS DE PRUEBA PEQUEÑA ESCALA</span>
      <div class="pub-authors">E. Cortés, G. Rodríguez, Ó. Ojeda, et al.</div>
      <p class="pub-excerpt">Desarrollo de giroscopio 3DOF y banco de aceleración 5g para validación de CubeSats.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/DISEÑO Y CONSTRUCCIÓN DE BANCOS DE PRUEBA PARA_SISTEMAS AEROESPACIALES DE PEQUEÑA ESCALA.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

  <div class="pub-card" data-year="2019">
    <span class="pub-badge">2019</span>
    <div class="pub-body">
      <span class="pub-title">ROVER DE PRUEBA PARA SUBSISTEMAS</span>
      <div class="pub-authors">Camilo Molina, Diego Mendoza, Omar López</div>
      <p class="pub-excerpt">Implementación de rover rocker-bogie para validación de algoritmos de mapeo planetario.</p>
    </div>
    <div class="pub-footer">
      <a class="btn-view" onclick="openVisor('{{ '/ARTICULOS/IMPLEMENTACION DE UN ROVER DE PRUEBA DE SUBSISTEMAS DE VEHÍCULOS DE EXPLORACIÓN NO TRIPULADOS.pdf' | relative_url }}')">Ver Documento</a>
    </div>
  </div>

</div>

<div id="visorPanel" class="modal-visor">
  <div class="modal-content">
    <span class="close-visor" onclick="closeVisor()">&times;</span>
    <iframe id="pdfIframe" src=""></iframe>
  </div>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // === 1. LÓGICA DEL HEADER ESPACIAL ===
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

    // === 2. LÓGICA DE FILTRADO Y VISOR ===
    // Definimos las funciones globalmente para que los botones onclick las encuentren
    window.filterPubs = function(year, btn) {
      const cards = document.querySelectorAll('.pub-card');
      const btns = document.querySelectorAll('.filter-btn');
      btns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      cards.forEach(card => {
        if (year === 'all' || card.getAttribute('data-year') === year) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });
    }

    window.openVisor = function(pdfPath) {
      document.getElementById('pdfIframe').src = pdfPath;
      document.getElementById('visorPanel').style.display = 'block';
      document.body.style.overflow = 'hidden';
    }

    window.closeVisor = function() {
      document.getElementById('visorPanel').style.display = 'none';
      document.getElementById('pdfIframe').src = '';
      document.body.style.overflow = 'auto';
    }

    // Cerrar visor con la tecla Escape
    window.onkeydown = function(event) {
      if (event.keyCode == 27) closeVisor();
    }
  });
</script>