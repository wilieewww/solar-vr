<!DOCTYPE html>
<html>
<head>
  <title>Sistema Solar VR</title>
  <script src="https://aframe.io/releases/1.4.0/aframe.min.js"></script>
  <style>
    #info-panel {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0,0,20,0.95);
      border: 2px solid #4fc3f7;
      border-radius: 15px;
      padding: 20px;
      color: white;
      font-family: Arial;
      z-index: 999;
      width: 80%;
      max-width: 350px;
      text-align: center;
    }
    #info-panel h2 { color: #FDB813; margin: 0 0 10px; font-size: 22px; }
    #info-panel p { font-size: 14px; line-height: 1.6; }
    #close-btn {
      background: #4fc3f7;
      border: none;
      color: #000;
      padding: 8px 20px;
      border-radius: 8px;
      font-size: 16px;
      margin-top: 10px;
      cursor: pointer;
      font-weight: bold;
    }
    #quiz-panel {
      display: none;
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0,0,20,0.95);
      border: 2px solid #FDB813;
      border-radius: 15px;
      padding: 15px;
      color: white;
      font-family: Arial;
      z-index: 999;
      width: 85%;
      max-width: 380px;
      text-align: center;
    }
    #quiz-panel h3 { color: #FDB813; margin: 0 0 10px; font-size: 16px; }
    .quiz-btn {
      display: block;
      width: 100%;
      background: #1a3a5c;
      border: 1px solid #4fc3f7;
      color: white;
      padding: 8px;
      border-radius: 8px;
      margin: 5px 0;
      font-size: 13px;
      cursor: pointer;
    }
    .quiz-btn:hover { background: #4fc3f7; color: #000; }
    #quiz-result { font-size: 15px; font-weight: bold; margin-top: 8px; }
    #quiz-next {
      background: #FDB813;
      border: none;
      color: #000;
      padding: 8px 20px;
      border-radius: 8px;
      font-size: 14px;
      margin-top: 8px;
      cursor: pointer;
      font-weight: bold;
      display: none;
    }
    #score {
      position: fixed;
      top: 15px;
      right: 15px;
      background: rgba(0,0,20,0.8);
      border: 1px solid #FDB813;
      color: #FDB813;
      padding: 8px 14px;
      border-radius: 10px;
      font-family: Arial;
      font-size: 14px;
      z-index: 998;
    }
    #hint {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0,0,0,0.7);
      color: #aaa;
      padding: 6px 14px;
      border-radius: 8px;
      font-family: Arial;
      font-size: 12px;
      z-index: 997;
    }
  </style>
</head>
<body>

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
