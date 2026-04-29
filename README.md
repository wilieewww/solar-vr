# solar-vr
<!DOCTYPE html>
<html>
  <head>
    <title>Sistema Solar VR</title>
    <script src="https://aframe.io/releases/1.4.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene background="color: #000011">

      <!-- Sol -->
      <a-sphere position="0 1.6 -5" radius="1.2" color="#FDB813"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 8000">
      </a-sphere>
      <a-text value="SOL\nEstrella central\nTemp: 5,500°C" 
        position="-0.8 3.2 -5" color="yellow" width="3"></a-text>

      <!-- Mercurio -->
      <a-sphere position="-4 1.6 -5" radius="0.2" color="#b5b5b5"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 3000">
      </a-sphere>
      <a-text value="MERCURIO\nMás cercano al Sol\nTemp: 430°C" 
        position="-5 2.5 -5" color="white" width="2.5"></a-text>

      <!-- Venus -->
      <a-sphere position="-6.5 1.6 -5" radius="0.35" color="#e8cda0"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 5000">
      </a-sphere>
      <a-text value="VENUS\nMás caliente del sistema\nTemp: 465°C" 
        position="-8 2.5 -5" color="white" width="2.5"></a-text>

      <!-- Tierra -->
      <a-sphere position="4 1.6 -5" radius="0.4" color="#1a6fbf"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 6000">
      </a-sphere>
      <a-text value="TIERRA\nNuestro hogar\nGravedad: 9.8 m/s²" 
        position="3 2.8 -5" color="#4fc3f7" width="2.5"></a-text>

      <!-- Marte -->
      <a-sphere position="7 1.6 -5" radius="0.3" color="#c1440e"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 7000">
      </a-sphere>
      <a-text value="MARTE\nPlaneta rojo\nGravedad: 3.7 m/s²" 
        position="6 2.8 -5" color="#ff7043" width="2.5"></a-text>

      <!-- Cámara VR -->
      <a-camera position="0 1.6 0" wasd-controls look-controls></a-camera>

    </a-scene>
  </body>
</html>
