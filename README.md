<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Sistema ÉTOS</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>🧠 Sistema <span class="neon">ÉTOS</span></h1>
    <p><strong>Nome do Caçador:</strong> Chefe</p>
    <p><strong>Nível:</strong> <span id="nivel">1</span></p>
    <p><strong>XP:</strong> <span id="xp">0</span>/100</p>

    <div class="xp-bar">
      <div id="xp-preenchido"></div>
    </div>

    <p><strong>Foco:</strong> <span id="foco">1</span></p>
    <p><strong>Disciplina:</strong> <span id="disciplina">1</span></p>
    <p><strong>Conhecimento:</strong> <span id="conhecimento">1</span></p>

    <h3>🎯 Missão do Dia</h3>
    <p>Estudar 30 minutos de Python</p>

    <button onclick="completarMissao()">✔️ Concluir Missão</button>
  </div>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: 'Segoe UI', sans-serif;
  background-color: #0a0a0a;
  color: #00ffee;
  text-align: center;
  margin: 0;
  padding: 20px;
}

.container {
  max-width: 500px;
  margin: auto;
  background: #111;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 0 30px #00ffee;
}

.neon {
  color: #00ffee;
  text-shadow: 0 0 10px #00ffee, 0 0 20px #00ffee;
}

.xp-bar {
  background: #333;
  border-radius: 10px;
  height: 20px;
  margin: 10px 0;
  overflow: hidden;
}

#xp-preenchido {
  height: 100%;
  background: linear-gradient(90deg, #00ffee, #00ffcc);
  width: 0%;
  border-radius: 10px;
  transition: width 0.5s ease-in-out;
}

button {
  background-color: #00ffee;
  color: #000;
  padding: 12px 25px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-weight: bold;
  margin-top: 15px;
  box-shadow: 0 0 15px #00ffee;
  transition: background 0.3s;
}

button:hover {
  background-color: #00ccdd;
}
let nivel = parseInt(localStorage.getItem("nivel")) || 1;
let xp = parseInt(localStorage.getItem("xp")) || 0;
let foco = parseInt(localStorage.getItem("foco")) || 1;
let disciplina = parseInt(localStorage.getItem("disciplina")) || 1;
let conhecimento = parseInt(localStorage.getItem("conhecimento")) || 1;

function atualizarTela() {
  document.getElementById("nivel").innerText = nivel;
  document.getElementById("xp").innerText = xp;
  document.getElementById("foco").innerText = foco;
  document.getElementById("disciplina").innerText = disciplina;
  document.getElementById("conhecimento").innerText = conhecimento;

  let porcentagem = (xp / 100) * 100;
  document.getElementById("xp-preenchido").style.width = `${porcentagem}%`;
}

function completarMissao() {
  xp += 25;
  foco += 1;
  disciplina += 1;
  conhecimento += 1;

  if (xp >= 100) {
    xp -= 100;
    nivel += 1;
  }

  localStorage.setItem("nivel", nivel);
  localStorage.setItem("xp", xp);
  localStorage.setItem("foco", foco);
  localStorage.setItem("disciplina", disciplina);
  localStorage.setItem("conhecimento", conhecimento);

  atualizarTela();
}

atualizarTela();
