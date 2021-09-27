<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { Player } from "./player";

  let player = new Player();
  const dispatch = createEventDispatcher();

  const submit = (e) => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = new Player();
  };
</script>

<form on:submit={submit} class="grid-3">
  <input type="text" bind:value={player.name} /><br />
  <input type="number" bind:value={player.score} />
  <button type="submit">Add</button>
</form>
