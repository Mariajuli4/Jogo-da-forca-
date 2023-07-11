<script>
// @ts-nocheck
import Modal from "./modal.svelte";
   let modal;
   let modal2;
</script>
<body> 
    <div class="container"> <!-- página inicial -->
      <h1>JOGO DA FORCA</h1>
      <p>Clique e divirta-se!</p>
      <button><a href="/página do jogo">Iniciar jogo</a></button>
      
      <button on:click={()=>modal.show()}>Sobre</button>
       <Modal bind:this={modal}> <!-- janela modal -->
        <h2>Projeto desenvolvido para finalização de período.</h2>
        <p>Desenvolvido por: <br>Maria Julia<br>Julio Pinto<br>Jhonnata Marcos<br>
        <button on:click={() => modal.hide()}>Voltar</button>
      </Modal>
      
      <button on:click={()=>modal2.show()}>Instruções</button>
     <Modal bind:this={modal2}> <!-- janela modal --> 
        <h2>Instruções</h2>
       <nav>
        <h3>A cada letra errada, um elemento de uma forca é desenhado, e o objetivo é adivinhar a palavra antes que o desenho esteja completo.</h3>
       </nav>
       <button on:click={() => modal2.hide()}>Voltar</button>
      </Modal>
     </div>
</body>
      
     <style>
    @font-face {
    font-family:cursive;
 }
    .container {
  text-align: center;
  margin-top: 200px;
  font-family:cursive;
}
h1 {
  
  font-size: 80px;
  margin-bottom: 20px;
  font-weight: normal;
}
button {
  padding: 10px 20px;
  font-size: 20px;
  background-color:yellow;
  color:black;
  border: 2px solid yellow;
 border-style: inherit;
  border-radius: 4px;
  font-family:cursive;
  }
button:hover{
    box-shadow: 0 0 15px rgb(70, 74, 75), inset 0 0 15px rgb(212, 221, 222);
  }
a{
  color: black;
  text-decoration: none;
 }
body{
  background-color: gray;
}
nav{
  font-size: 25px;
}
p{
  font-size: 20px;
}

</style>