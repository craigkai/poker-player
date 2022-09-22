<script>
  export let session;

  let players = ["Craig"];
</script>

<table class="table-auto">
  <thead>
    <tr>
      <th>Player</th>
      <th>Buy In</th>
    </tr>
  </thead>
  <tbody>
    {#each players as player}
      <tr>
        <td>{player}</td>
        <td>N/A</td>
      </tr>
    {/each}
  </tbody>
</table>

{#if session}
  Can Edit
{/if}
