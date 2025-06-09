# sistema-etos
O SISTEMA
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Sistema ÉTOS</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>🧠 Sistema ÉTOS</h1>
    <p>Nome do Caçador: <span id="nome">Chefe</span></p>

    <div class="status">
      <p>Nível: <span id="nivel">1</span></p>
      <p>XP: <span id="xp">0</span>/100</p>
      <div class="xp-bar"><div id="xp-preenchido"></div></div>
      <p>Foco: <span id="foco">1</span></p>
      <p>Disciplina: <span id="disciplina">1</span></p>
      <p>Conhecimento: <span id="conhecimento">1</span></p>
    </div>

    <div class="missao">
      <h2>Missão do Dia</h2>
      <p id="missao-texto">Estudar 30 minutos de Python</p>
      <button onclick="completarMissao()">✔️ Concluir Missão</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  background-color: #0f0f0f;
  color: #00ffcc;
  text-align: center;
  padding: 20px;
}

.container {
  max-width: 500px;
  margin: auto;
  background: #1a1a1a;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 0 15px #00ffcc;
}

.xp-bar {
  background: #333;
  border-radius: 10px;
  height: 20px;
  margin: 10px 0;
}

#xp-preenchido {
  height: 100%;
  background: #00ffcc;
  width: 0%;
  border-radius: 10px;
}

button {
  background-color: #00ffcc;
  color: #000;
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-weight: bold;
  margin-top: 10px;
}

button:hover {
  background-color: #00ffaa;
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

  // Salvar no navegador
  localStorage.setItem("nivel", nivel);
  localStorage.setItem("xp", xp);
  localStorage.setItem("foco", foco);
  localStorage.setItem("disciplina", disciplina);
  localStorage.setItem("conhecimento", conhecimento);

  atualizarTela();
}

atualizarTela();
