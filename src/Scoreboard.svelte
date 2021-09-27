<script lang="ts">
  import type { Player } from "./player";
  import AddPlayer from "./AddPlayer.svelte";
  import Scorecard from "./Scorecard.svelte";

  let players: Player[] = [
    { name: "Nithsua", score: 69 },
    { name: "Paulos El Macho", score: 87 },
    { name: "Loki", score: 96 },
  ];

  const addPlayer = (e: CustomEvent) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const deletePlayer = (e: CustomEvent) => {
    const newPlayer = e.detail;
    players.filter((player, index) => newPlayer == player);
  };
</script>

<div class="Container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length == 0}
    <h1>No players</h1>
  {:else}
    {#each players as player}
      <Scorecard name={player.name} score={player.score} />
    {/each}
  {/if}
</div>

<style>
</style>
