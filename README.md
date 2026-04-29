<div id="container">
  <div id="loading">
    <div class="spinner"></div>
    <h2>Loading Solar System...</h2>
    <p>Initializing 3D environment and planetary data</p>
  </div>

  <div id="ui-container">
    <h1 id="title">3D Solar System Explorer</h1>

    <div id="instructions">
      <h3>Controls</h3>
      <ul>
        <li>Click on planets to select them</li>
        <li>Use mouse to rotate the view</li>
        <li>Scroll to zoom in/out</li>
        <li>Adjust time speed with the slider</li>
        <li>Use planet buttons for quick navigation</li>
      </ul>
    </div>

    <div id="planet-info">
      <h2><span class="planet-icon" id="selected-planet-icon"></span> <span id="selected-planet-name">Planet Name</span></h2>
      <div class="info-row">
        <span class="info-label">Type:</span>
        <span class="info-value" id="planet-type">Terrestrial</span>
      </div>
      <div class="info-row">
        <span class="info-label">Diameter:</span>
        <span class="info-value" id="planet-diameter">12,742 km</span>
      </div>
      <div class="info-row">
        <span class="info-label">Distance from Sun:</span>
        <span class="info-value" id="planet-distance">149.6 million km</span>
      </div>
      <div class="info-row">
        <span class="info-label">Orbital Period:</span>
        <span class="info-value" id="planet-period">365.25 days</span>
      </div>
      <div class="info-row">
        <span class="info-label">Moons:</span>
        <span class="info-value" id="planet-moons">1</span>
      </div>
      <div class="info-row">
        <span class="info-label">Description:</span>
      </div>
      <p id="planet-description">Planet description goes here...</p>
    </div>

    <div id="planet-selector">
      <!-- Planet buttons will be generated here -->
    </div>

    <div id="controls">
      <div class="control-group">
        <button id="play-pause">⏸️ Pause</button>
        <button id="reset-view">Reset View</button>
      </div>

      <div class="control-group" id="time-control">
        <span>Time Speed:</span>
        <input type="range" id="time-slider" min="0" max="200" value="10">
        <span id="time-factor">1x</span>
      </div>
    </div>
  </div>
</div>
  <div id="score">⭐ Puntos: <span id="pts">0</span></div>
  <div id="hint">👆 Toca un planeta para explorar</div>

  <!-- INFO PANEL -->
  <div id="info-panel">
    <h2 id="info-title"></h2>
    <p id="info-body"></p>
    <button id="close-btn" onclick="closeInfo()">Cerrar ✕</button>
  </div>

  <!-- QUIZ PANEL -->
  <div id="quiz-panel">
    <h3 id="quiz-q"></h3>
    <div id="quiz-options"></div>
    <div id="quiz-result"></div>
    <button id="quiz-next" onclick="nextQuestion()">Siguiente ➜</button>
  </div>

  <a-scene background="color: #000011">

    <!-- SOL -->
    <a-sphere id="sol" position="0 1.6 -5" radius="1.1" color="#FDB813"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 10000"
      class="planet" onclick="showInfo('SOL','☀️ Estrella central del sistema solar.\n🌡️ Temperatura superficial: 5,500°C\n📏 Diámetro: 1,392,000 km\n⚡ Tipo: Enana amarilla G2')">
    </a-sphere>
    <a-text value="SOL" position="-0.2 3 -5" color="#FDB813" width="3.5"></a-text>

    <!-- MERCURIO -->
    <a-sphere position="-3 1.6 -5" radius="0.18" color="#b5b5b5"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 2000"
      class="planet" onclick="showInfo('MERCURIO','🪨 Planeta más pequeño y cercano al Sol.\n🌡️ Temperatura: -180°C a 430°C\n📏 Diámetro: 4,879 km\n📅 Año: 88 días terrestres')">
    </a-sphere>
    <a-text value="MERCURIO" position="-3.8 2.2 -5" color="white" width="2.5"></a-text>

    <!-- VENUS -->
    <a-sphere position="-5 1.6 -4" radius="0.3" color="#e8cda0"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 4000"
      class="planet" onclick="showInfo('VENUS','🌫️ El planeta más caliente del sistema.\n🌡️ Temperatura: 465°C\n📏 Diámetro: 12,104 km\n🔄 Gira al revés comparado con la Tierra')">
    </a-sphere>
    <a-text value="VENUS" position="-5.8 2.2 -4" color="#e8cda0" width="2.5"></a-text>

    <!-- TIERRA -->
    <a-sphere position="3 1.6 -5" radius="0.35" color="#1a6fbf"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 5000"
      class="planet" onclick="showInfo('TIERRA','🌍 Nuestro hogar, único con vida conocida.\n🌡️ Temperatura media: 15°C\n⚡ Gravedad: 9.8 m/s²\n💧 71% cubierto de agua')">
    </a-sphere>
    <a-text value="TIERRA" position="2.3 2.3 -5" color="#4fc3f7" width="2.5"></a-text>

    <!-- MARTE -->
    <a-sphere position="5 1.6 -4" radius="0.25" color="#c1440e"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 6000"
      class="planet" onclick="showInfo('MARTE','🔴 El planeta rojo, posible futuro hogar.\n🌡️ Temperatura: -63°C promedio\n⚡ Gravedad: 3.7 m/s²\n🏔️ Monte Olimpo: volcán más alto del sistema')">
    </a-sphere>
    <a-text value="MARTE" position="4.3 2.2 -4" color="#ff7043" width="2.5"></a-text>

    <!-- JÚPITER -->
    <a-sphere position="0 1.6 -9" radius="0.9" color="#c88b3a"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 3000"
      class="planet" onclick="showInfo('JÚPITER','🟠 El planeta más grande del sistema solar.\n📏 Diámetro: 139,820 km\n🌪️ Gran Mancha Roja: tormenta de 350 años\n🛰️ Tiene 95 lunas conocidas')">
    </a-sphere>
    <a-text value="JÚPITER" position="-0.8 2.8 -9" color="#c88b3a" width="3"></a-text>

    <!-- SATURNO -->
    <a-sphere position="-5 1.6 -9" radius="0.75" color="#e4d191"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 4000"
      class="planet" onclick="showInfo('SATURNO','💍 Famoso por sus anillos de hielo y roca.\n📏 Diámetro: 116,460 km\n⚡ Gravedad: 10.4 m/s²\n🛰️ Su luna Titán tiene atmósfera densa')">
    </a-sphere>
    <!-- Anillo de Saturno -->
    <a-torus position="-5 1.6 -9" radius="1.1" radius-tubular="0.05" color="#c8b560"
      rotation="75 0 0">
    </a-torus>
    <a-text value="SATURNO" position="-6 2.7 -9" color="#e4d191" width="3"></a-text>

    <!-- URANO -->
    <a-sphere position="5 1.6 -9" radius="0.5" color="#7de8e8"
      animation="property: rotation; to: 0 360 0; loop: true; dur: 5000"
      class="planet" onclick="showInfo('URANO','🔵 Planeta de hielo, gira de lado.\n🌡️ Temperatura: -224°C\n📏 Diámetro: 50,724 km\n↩️ Su eje está inclina
