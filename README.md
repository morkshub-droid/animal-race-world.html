<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Animal Race World – Explorador</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #0e0e11;
      color: #ffffff;
    }header {
  padding: 18px;
  text-align: center;
  background: #111827;
  border-bottom: 1px solid #1f2937;
}

header h1 {
  margin: 0;
  font-size: 1.8rem;
}

header p {
  margin-top: 6px;
  font-size: 0.9rem;
  color: #9ca3af;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
  gap: 16px;
  padding: 20px;
}

.card {
  background: #111827;
  border-radius: 14px;
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  border: 1px solid #1f2937;
}

.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 30px rgba(0,0,0,0.6);
}

.card img {
  width: 100%;
  height: 130px;
  object-fit: cover;
  display: block;
}

.card h3 {
  margin: 0;
  padding: 10px;
  font-size: 1rem;
  text-align: center;
}

.modal {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.75);
  display: none;
  align-items: center;
  justify-content: center;
  z-index: 100;
}

.modal.active { display: flex; }

.modal-content {
  background: #0f172a;
  border-radius: 18px;
  max-width: 420px;
  width: 92%;
  overflow: hidden;
  border: 1px solid #1f2937;
  animation: pop 0.25s ease;
}

@keyframes pop {
  from { transform: scale(0.9); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

.modal-content img {
  width: 100%;
  height: 220px;
  object-fit: cover;
}

.modal-body {
  padding: 16px;
}

.modal-body h2 {
  margin: 0 0 10px;
}

.modal-body p {
  margin: 6px 0;
  font-size: 0.9rem;
  color: #d1d5db;
}

.close {
  text-align: center;
  padding: 12px;
  cursor: pointer;
  background: #020617;
  color: #60a5fa;
  font-weight: bold;
}

footer {
  padding: 12px;
  text-align: center;
  font-size: 0.8rem;
  color: #9ca3af;
}

  </style>
</head>
<body><header>
  <h1>Animal Race World</h1>
  <p>Explorador visual simple de animales</p>
</header><div class="grid" id="grid"></div><div class="modal" id="modal">
  <div class="modal-content">
    <img id="modalImg" />
    <div class="modal-body">
      <h2 id="modalName"></h2>
      <p><strong>Hábitat:</strong> <span id="modalHabitat"></span></p>
      <p><strong>Cómo vive:</strong> <span id="modalLive"></span></p>
      <p><strong>Nivel de peligro:</strong> <span id="modalDanger"></span></p>
    </div>
    <div class="close" onclick="closeModal()">Cerrar</div>
  </div>
</div><footer>
  Animal Race World · Explorador básico v1
</footer><script>
  const animals = [
    {
      name: 'León',
      img: 'https://images.unsplash.com/photo-1546182990-dffeafbe841d',
      habitat: 'Sabana africana',
      live: 'En manadas, cazando en grupo',
      danger: 'Peligroso'
    },
    {
      name: 'Tiburón Blanco',
      img: 'https://images.unsplash.com/photo-1501594907352-04cda38ebc29',
      habitat: 'Océanos templados',
      live: 'Depredador solitario',
      danger: 'Extremadamente mortal'
    },
    {
      name: 'Lobo',
      img: 'https://images.unsplash.com/photo-1500530855697-b586d89ba3ee',
      habitat: 'Bosques y montañas',
      live: 'Manadas organizadas',
      danger: 'Normal'
    },
    {
      name: 'Águila',
      img: 'https://images.unsplash.com/photo-1503264116251-35a269479413',
      habitat: 'Montañas y cielos abiertos',
      live: 'Caza desde el aire',
      danger: 'Normal'
    }
  ];

  const grid = document.getElementById('grid');
  const modal = document.getElementById('modal');

  animals.forEach(a => {
    const card = document.createElement('div');
    card.className = 'card';
    card.innerHTML = `<img src="${a.img}" alt="${a.name}"><h3>${a.name}</h3>`;
    card.onclick = () => openModal(a);
    grid.appendChild(card);
  });

  function openModal(a) {
    document.getElementById('modalImg').src = a.img;
    document.getElementById('modalName').textContent = a.name;
    document.getElementById('modalHabitat').textContent = a.habitat;
    document.getElementById('modalLive').textContent = a.live;
    document.getElementById('modalDanger').textContent = a.danger;
    modal.classList.add('active');
  }

  function closeModal() {
    modal.classList.remove('active');
  }
</script></body>
</html>
