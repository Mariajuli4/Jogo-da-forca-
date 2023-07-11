<script>
	const frutas = [
	  "maça",
	  "banana",
	  "laranja",
	  "uva",
	  "melancia",
	  "abacaxi",
	  "morango",
	  "mirtilo",
	  "pêssego",
	  "manga",
	  "cereja",
	  "pera",
	  "kiwi",
	  "ameixa",
	  "limao",
	  "coco",
	  "framboesa",
	  "amora",
	  "papaya",
	  "damasco",
	  "figo",
	  "abacate",
	  "melao",
	  "lima",
	  "goiaba",
	  
	];
	const palavraSecreta =
	  frutas[Math.floor(Math.random() * frutas.length)];
	const letrasErradas = [];
	const letrasCorretas = [];
  
	document.addEventListener("keydown", (evento) => {
	  const codigo = evento.keyCode; // 65 - 90 (intervalo)
	  if (isLetra(codigo)) {
		const letra = evento.key;
		if (letrasErradas.includes(letra)) {
		  mostrarAvisoLetraRepetida();
		} else {
		  if (palavraSecreta.includes(letra)) {
			letrasCorretas.push(letra);
		  } else {
			letrasErradas.push(letra);
		  }
		}
		atualizarJogo();
	  }
	});
  
	function atualizarJogo() {
	  mostrarLetrasErradas();
	  mostrarLetrasCertas();
	  desenharForca();
	  checarJogo();
	}
  
	function mostrarLetrasErradas() {
	  const div = document.querySelector(".letras-erradas-container");
	  div.innerHTML = "<h3>Letras erradas</h3>";
	  letrasErradas.forEach((letra) => {
		div.innerHTML += `<span>${letra}</span>`;
	  });
	}
  
	function mostrarLetrasCertas() {
	  const container = document.querySelector(".palavra-secreta-container");
	  container.innerHTML = "";
	  palavraSecreta.split("").forEach((letra) => {
		if (letrasCorretas.includes(letra)) {
		  container.innerHTML += `<span>${letra}</span>`;
		} else {
		  container.innerHTML += `<span>_</span>`;
		}
	  });
	}
  
	function checarJogo() {
	  let mensagem = "";
	  const container = document.querySelector(".palavra-secreta-container");
	  const partesCorpo = document.querySelectorAll(".forca-parte");
  
	  if (letrasErradas.length === partesCorpo.length) {
		mensagem = "Fim de jogo! Você perdeu!";
	  }
  
	  if (palavraSecreta === container.innerText) {
		mensagem = "Parabéns! Você ganhou!";
	  }
  
	  if (mensagem) {
		document.querySelector("#mensagem").innerHTML = mensagem;
		document.querySelector(".popup-container").style.display = "flex";
	  }
	}
  
	function desenharForca() {
	  const partesCorpo = document.querySelectorAll(".forca-parte");
	  for (let i = 0; i < letrasErradas.length; i++) {
		partesCorpo[i].style.display = "block";
	  }
	}
  
	function mostrarAvisoLetraRepetida() {
	  const aviso = document.querySelector(".aviso-palavra-repetida");
	  aviso.classList.add("show");
	  setTimeout(() => {
		aviso.classList.remove("show");
	  }, 1000);
	}
  
	function isLetra(codigo) {
	  return codigo >= 65 && codigo <= 90;
	}
  
	function reiniciarJogo() {
	  window.location.reload();
	}
  </script>
  
  <body>
	<h1>Jogo da forca</h1>
	<h2>Digite no teclado uma letra e tente adivinhar a palavra!</h2>
        <h2>Dica: Frutas</h2>
	<div class="jogo-container">
	  <div class="forca-container">
		<svg height="250" width="200" class="forca">
		  <!-- forca -->
		  <line x1="60" y1="20" x2="140" y2="20" />
		  <line x1="140" y1="20" x2="140" y2="50" />
		  <line x1="60" y1="20" x2="60" y2="230" />
		  <line x1="20" y1="230" x2="100" y2="230" />
  
		  <!-- cabeça -->
		  <circle cx="140" cy="70" r="20" class="forca-parte" />
		  <!-- corpo -->
		  <line x1="140" y1="90" x2="140" y2="150" class="forca-parte" />
		  <!-- braços -->
		  <line x1="140" y1="120" x2="120" y2="100" class="forca-parte" />
		  <line x1="140" y1="120" x2="160" y2="100" class="forca-parte" />
		  <!-- pernas -->
		  <line x1="140" y1="150" x2="120" y2="180" class="forca-parte" />
		  <line x1="140" y1="150" x2="160" y2="180" class="forca-parte" />
		</svg>
	  </div>
  
	  <div class="letras-erradas-container">
		<h3>Letras erradas</h3>
	  </div>
	</div>
  
	<div class="palavra-secreta-container" />
  
	<div class="aviso-palavra-repetida">
	  <p>Você já usou essa letra!</p>
	</div>
  
	<div class="popup-container">
	  <div class="popup">
		<h2 id="mensagem" />
		<button id="btn-jogar" on:click={reiniciarJogo}> Jogar novamente </button>
	  </div>





	<script src="script.js"></script>
  </body>
  
  <style>
	body {
	  display: flex;
	  flex-direction: column;
	  align-items: center;
	  width: 100vw;
	  height: 100vh;
	  overflow: hidden;
	  background-color:gray;
	  color: black;
	  font-family:cursive
	}
  
	.jogo-container {
	  display: flex;
	  justify-content: space-evenly;
	  width: 100%;
	}
  
	.forca {
	  fill: transparent;
	  stroke: yellow;
	  stroke-width: 4px;
	  stroke-linecap: round;
	}
  
	.forca-parte {
	  display: none;
	}
  
	.letras-erradas-container {
	  font-size: 32px;
	}
  
	.letras-erradas-container span {
	  margin: 0 2px;
	}
  
	.palavra-secreta-container {
	  font-size: 45px;
	}
  
	.aviso-palavra-repetida {
	  background-color: rgba(0, 0, 0, 0.3);
	  border-radius: 10px 10px 0 0;
	  padding: 15px 20px;
	  position: absolute;
	  bottom: -55px;
	  transition: transform 0.3s ease-in-out;
	}
  
	.aviso-palavra-repetida p {
	  margin: 0;
	}
  
	.aviso-palavra-repetida.show {
	  transform: translateY(-50px);
	}
  
	.palavra-secreta-container span {
	  margin: 0 5px;
	}
  
	.popup-container {
	  background-color: rgba(0, 0, 0, 0.849);
	  position: fixed;
	  top: 0;
	  bottom: 0;
	  left: 0;
	  right: 0;
	  /* display: flex; */
	  display: none;
	  align-items: center;
	  justify-content: center;
	}
  
	.popup {
	  background: yellow;
	  border-radius: 5px;
	  box-shadow: 0 15px 10px 3px rgba(0, 0, 0, 0.1);
	  padding: 20px;
	  text-align: center;
	}
  
	.popup button {
	  cursor: pointer;
	  background-color: gray;
	  border: 0;
	  margin-top: 20px;
	  padding: 12px 20px;
	  font-size: 16px;
	}
  </style>
  
