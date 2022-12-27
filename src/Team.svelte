<script>
  export let teamName;
  export let points;
  export let gameOver;
  function add() {
    points += 1;
  }
  function minus() {
    points -= 1;
  }
</script>

<div class="col" style="border: dashed 5px {teamName.toLowerCase()}">
  <h2
    class:text-primary={teamName === 'Blue'}
    class:text-danger={teamName === 'Red'}
  >
    {teamName}: {points}
  </h2>
  <button disabled={gameOver} on:click={minus} class="btn btn-danger">-</button>
  <button disabled={gameOver} on:click={add} class="btn btn-success">+</button>
</div>

<style>
  div {
    text-align: center;
    padding: 30px;
  }
</style>
