<script>
  import Team from './Team.svelte';
  let redScore = 20;
  let blueScore = 20;
  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;
  $: btnRestText = gameOver ? 'New Game' : 'Reset Game';
  function resetGame() {
    redScore = 20;
    blueScore = 20;
  }
</script>

<div class="row mb-5">
  <div class="col">
    <h1 class="text-center">MTG Counter App</h1>
  </div>
</div>
<div class="row">
  <Team {gameOver} teamName="Red" bind:points={redScore} />
  <Team {gameOver} teamName="Blue" bind:points={blueScore} />
</div>
{#if gameOver}
  <div class="row mt-3 mb-3">
    <div class="col">
      {#if redWon}
        <h2 class="text-center text-danger">Red Won</h2>
      {:else}
        <h2 class="text-center text-primary">Blue Won</h2>
      {/if}
    </div>
  </div>
{/if}
<div class="row mt-3">
  <div class="col">
    <button
      on:click={resetGame}
      class:btn-success={gameOver}
      class:btn-warning={!gameOver}
      class="btn w-100">{btnRestText}</button
    >
  </div>
</div>
