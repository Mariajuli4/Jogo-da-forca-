<script>
    let shown= false;
   export function show(){
        shown = true;
 }
 export function hide(){
   shown = false;
 }
</script>

<svelte:window
on:keydown={ (e) => {
    if(e.keyCode == 27){
        hide();
    }
    }}/>

{#if shown}
<div class="modal-wrapper">
 <div class="modal">
     <slot />
    </div>
</div>
{/if}

<style>
  .modal-wrapper{
    background-color: gray;
    position: fixed;
    width: 100%;
    height: 100%;
    top:0;
    left: 0;
  }
  .modal{
      background-color:rgb(255, 255, 255);
      padding: 1rem;
      margin: 10% auto;
    border-style: solid;
  }
  </style>