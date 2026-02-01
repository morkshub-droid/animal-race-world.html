<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Animal Race World – Enciclopedia de Animales</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      color: #fff;
      overflow-x: hidden;
    }
    header {
      padding: 20px;
      text-align: center;
      background: rgba(0,0,0,0.3);
    }
    header h1 { margin: 0; font-size: 2rem; }
    header p { opacity: 0.8; }/* Área de burbujas */
#world {
  position: relative;
  width: 100%;
  height: 70vh;
  overflow: hidden;
}

.bubble {
  position: absolute;
  width: 90px;
  height: 90px;
  border-radius: 50%;
  background: rgba(255,255,255,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: transform 0.3s, background 0.3s;
  backdrop-filter: blur(4px);
}
.bubble:hover {
  transform: scale(1.2);
  background: rgba(255,255,255,0.35);
}

.bubble span {
  text-align: center;
  font-size: 0.8rem;
  pointer-events: none;
}

/* Panel de información */
#info {
  position: fixed;
  right: 0;
  top: 0;
  width: 320px;
  height: 100vh;
  background: #111;
  padding: 20px;
  overflow-y: auto;
  transform: translateX(100%);
  transition: transform 0.4s ease;
}
#info.active {
  transform: translateX(0);
}
#info h2 { margin-top: 0; }
.tag {
  display: inline-block;
  padding: 4px 8px;
  border-radius: 12px;
  background: #333;
  font-size: 0.7rem;
  margin-right: 6px;
  margin-bottom: 6px;
}
.danger {
  margin-top: 10px;
  font-weight: bold;
}

footer {
  padding: 10px;
  text-align: center;
  background: rgba(0,0,0,0.3);
  font-size: 0.8rem;
}

  </style>
</head>
<body><header>
  <h1>🌍 Animal Race World</h1>
  <p>Enciclopedia interactiva de todos los animales del mundo</p>
</header><div id="world"></div><div id="info">
  <h2 id="name"></h2>
  <div id="tags"></div>
  <p><strong>Ventaja:</strong> <span id="ventaja"></span></p>
  <p><strong>Cómo sobrevive:</strong> <span id="sobrevive"></span></p>
  <p><strong>Año de descubrimiento:</strong> <span id="anio"></span></p>
  <p><strong>Cómo vive ahora:</strong> <span id="viveAhora"></span></p>
  <p><strong>Cómo vivía antes:</strong> <span id="viveAntes"></span></p>
  <p class="danger">⚠ Nivel de peligro: <span id="peligro"></span></p>
</div><footer>
  Proyecto educativo – puedes ampliarlo con miles de animales 🐾
</footer><script>
  // Base de datos de ejemplo (se puede ampliar a miles)
  const animals = [
    {
      name: "Lobo",
      ventaja: "Caza en manada",
      sobrevive: "Trabajo en equipo y gran resistencia",
      anio: "1758",
      viveAhora: "Bosques y montañas",
      viveAntes: "Regiones mucho más amplias del hemisferio norte",
      peligro: "Normal",
      tags: ["Mamífero", "Carnívoro", "Salvaje"]
    },
    {
      name: "Perro",
      ventaja: "Inteligencia y lealtad",
      sobrevive: "Conviviendo con humanos",
      anio: "Domesticado hace ~15,000 años",
      viveAhora: "Hogares humanos",
      viveAntes: "Descendiente del lobo",
      peligro: "Común",
      tags: ["Mamífero", "Doméstico", "Razas múltiples"]
    },
    {
      name: "Tiburón Blanco",
      ventaja: "Sentidos ultra desarrollados",
      sobrevive: "Depredador tope del océano",
      anio: "1758",
      viveAhora: "Océanos templados",
      viveAntes: "Océanos prehistóricos",
      peligro: "Extremadamente mortal",
      tags: ["Pez", "Marino", "Depredador"]
    }
  ];

  const world = document.getElementById('world');
  const info = document.getElementById('info');

  animals.forEach(animal => {
    const bubble = document.createElement('div');
    bubble.className = 'bubble';
    bubble.style.left = Math.random() * 90 + '%';
    bubble.style.top = Math.random() * 85 + '%';

    const label = document.createElement('span');
    label.textContent = animal.name;
    bubble.appendChild(label);

    bubble.addEventListener('click', () => showInfo(animal));
    world.appendChild(bubble);
  });

  function showInfo(animal) {
    document.getElementById('name').textContent = animal.name;
    document.getElementById('ventaja').textContent = animal.ventaja;
    document.getElementById('sobrevive').textContent = animal.sobrevive;
    document.getElementById('anio').textContent = animal.anio;
    document.getElementById('viveAhora').textContent = animal.viveAhora;
    document.getElementById('viveAntes').textContent = animal.viveAntes;
    document.getElementById('peligro').textContent = animal.peligro;

    const tagsDiv = document.getElementById('tags');
    tagsDiv.innerHTML = '';
    animal.tags.forEach(t => {
      const tag = document.createElement('span');
      tag.className = 'tag';
      tag.textContent = t;
      tagsDiv.appendChild(tag);
    });

    info.classList.add('active');
  }
</script></body>
</html>
