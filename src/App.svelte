<script>
  import Team from "./Team.svelte";
  let blueScore = 20;
  let redScore = 20;
  let winningText = '';
  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;
  $: if(blueWon){
    winningText = "blue Won!";
  } else {
    winningText = "Red Won!";
  }
  function newGame(){
    blueScore = 20;
    redScore = 20;
  }
</script>
<div class="row">
  <div class="col">
    <h1 class="text-center">MTG Counter</h1>
  </div>
</div>
<div class="row">
  <div class="col">
    <Team {gameOver} team="Red" bind:score={redScore}/>
    <Team {gameOver} team="blue" bind:score={blueScore} />
  </div>
</div>

{#if !gameOver}
<div class="row mt-3">
  <div class="col">
    <button on:click={newGame} class="btn btn-warning">Reset Game</button>
  </div>
</div>
{:else}
<div class="row">
  <div class="col">
    {#if blueWon}
      <h2 class="text-center text-primary">Blue Won</h2>
    {:else}
      <h2 class="text-center text-danger">Red Won!</h2>
    {/if}
  </div>
</div>
<div class="row mt-3">
  <button on:click={newGame} class="btn btn-success">New Game</button>
</div>
{/if}