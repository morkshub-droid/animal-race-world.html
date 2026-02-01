<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Animal Race World</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: 'Segoe UI', system-ui, sans-serif;
      background: radial-gradient(circle at top, #0b2d3a, #000);
      color: #fff;
      overflow-x: hidden;
    }header {
  padding: 20px;
  text-align: center;
  background: rgba(0,0,0,0.6);
  backdrop-filter: blur(6px);
  position: sticky;
  top: 0;
  z-index: 10;
}

header h1 {
  margin: 0;
  font-size: 2.3rem;
  letter-spacing: 1px;
}

header p {
  margin-top: 6px;
  opacity: 0.85;
  font-size: 0.95rem;
}

#world {
  position: relative;
  width: 100%;
  height: 75vh;
  overflow: hidden;
}

.bubble {
  position: absolute;
  width: 95px;
  height: 95px;
  border-radius: 50%;
  background: radial-gradient(circle at top left, rgba(255,255,255,0.45), rgba(255,255,255,0.1));
  box-shadow: 0 0 20px rgba(0,255,255,0.25);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  animation: float 6s ease-in-out infinite;
  transition: transform 0.35s ease, box-shadow 0.35s ease;
}

.bubble:hover {
  transform: scale(1.25);
  box-shadow: 0 0 35px rgba(0,255,255,0.7);
}

.bubble span {
  text-align: center;
  font-size: 0.75rem;
  font-weight: 600;
  pointer-events: none;
  padding: 6px;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-18px); }
}

#info {
  position: fixed;
  right: 0;
  top: 0;
  width: 340px;
  height: 100vh;
  background: linear-gradient(180deg, #111, #000);
  padding: 22px;
  overflow-y: auto;
  transform: translateX(100%);
  transition: transform 0.45s ease;
  box-shadow: -10px 0 40px rgba(0,0,0,0.7);
  z-index: 20;
}

#info.active { transform: translateX(0); }

#info h2 {
  margin-top: 0;
  font-size: 1.8rem;
}

.tags { margin-bottom: 10px; }

.tag {
  display: inline-block;
  padding: 5px 10px;
  border-radius: 14px;
  background: #1e1e1e;
  font-size: 0.7rem;
  margin: 4px 4px 0 0;
  border: 1px solid #333;
}

.danger {
  margin-top: 14px;
  padding: 10px;
  border-radius: 10px;
  background: #220000;
  color: #ff4d4d;
  font-weight: bold;
  text-align: center;
}

footer {
  padding: 14px;
  text-align: center;
  background: rgba(0,0,0,0.5);
  font-size: 0.8rem;
  opacity: 0.85;
}

  </style>
</head>
<body><header>
  <h1>🌍 Animal Race World</h1>
  <p>La enciclopedia interactiva definitiva de todos los animales y sus razas</p>
</header><div id="world"></div><div id="info">
  <h2 id="name"></h2>
  <div class="tags" id="tags"></div>
  <p><strong>Ventaja:</strong> <span id="ventaja"></span></p>
  <p><strong>Cómo sobrevive:</strong> <span id="sobrevive"></span></p>
  <p><strong>Año de descubrimiento:</strong> <span id="anio"></span></p>
  <p><strong>Cómo vive ahora:</strong> <span id="viveAhora"></span></p>
  <p><strong>Cómo vivía antes:</strong> <span id="viveAntes"></span></p>
  <div class="danger">⚠ Nivel de peligro: <span id="peligro"></span></div>
</div><footer>
  © Animal Race World – Proyecto educativo y exploratorio
</footer><script>
  const animals = [
    {
      name: "Perro",
      ventaja: "Lealtad e inteligencia",
      sobrevive: "Conviviendo con humanos",
      anio: "Domesticado hace ~15,000 años",
      viveAhora: "Hogares humanos",
      viveAntes: "Descendiente directo del lobo",
      peligro: "Común",
      tags: ["Mamífero", "Doméstico", "Muchas razas"]
    },
    {
      name: "Lobo",
      ventaja: "Caza en manada",
      sobrevive: "Trabajo en equipo y resistencia",
      anio: "1758",
      viveAhora: "Bosques y montañas",
      viveAntes: "Amplias regiones del hemisferio norte",
      peligro: "Normal",
      tags: ["Mamífero", "Salvaje", "Carnívoro"]
    },
    {
      name: "Tiburón Blanco",
      ventaja: "Sentidos extremadamente desarrollados",
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
    bubble.style.left = Math.random() * 88 + '%';
    bubble.style.top = Math.random() * 80 + '%';

    const label = document.createElement('span');
    label.textContent = animal.name;
    bubble.appendChild(label);

    bubble.onclick = () => showInfo(animal);
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
    animal.tags.forEach(tagText => {
      const tag = document.createElement('span');
      tag.className = 'tag';
      tag.textContent = tagText;
      tagsDiv.appendChild(tag);
    });

    info.classList.add('active');
  }
</script></body>
</html>
