<script lang="ts">
  export let name: string;
  export let score: number;
  let showControls: boolean = false;

  const addPoint = () => (score += 1);
  const removePoint = () => (score -= 1);
  const toggleShowControl = () => (showControls = !showControls);
</script>

<div class="card">
  <div>
    <h1>{name}</h1>
    <button class="btn" on:click={toggleShowControl}
      >{showControls ? "<" : ">"}</button
    ><br />
    Score: {score}
  </div>
  {#if showControls}
    <button class="btn" on:click={addPoint}> + </button>
    <button class="btn-alert" on:click={removePoint}> - </button><br />
    <input type="number" bind:value={score} />
  {/if}
</div>

<style>
  .card {
    max-width: 400px;
    padding: 10px;
    margin: 8px;
    border: 1px solid;
    border-radius: 15px;
  }

  .btn {
    aspect-ratio: 2;
    padding: 8px;
  }

  .btn-alert {
    aspect-ratio: 2;
    padding: 8px;
    background-color: grey;
  }
</style>
