<script lang="ts">
  export let data = [];
  export let columns: any[] = [];
  export let show_rows = true;
	
  let newRow = [...columns];

  function addColumn() {
    columns = columns.push("New Column");
  }
	
	function addRow() {
		data = [...data, [...newRow]]
		newRow = columns
	}
	
	/**
   * @param {string} rowToBeDeleted
   */
	function deleteRow(rowToBeDeleted: string) {
		data = data.filter(row => row != rowToBeDeleted)
	}
</script>

<table class="table-auto">
	<tr>
		{#each columns as column}
			<th>{column}</th>
		{/each}
	</tr>
	
	{#each data as row}
		<tr>
			{#each row as cell}
			<td contenteditable="true" bind:innerHTML={cell} />
			{/each}
			<button on:click={() => deleteRow(row)}>
				X
			</button>
		</tr>
	{/each}

  {#if show_rows}
    <tr class="new">
      {#each newRow as column}
        <td contenteditable="true" bind:innerHTML={column} />
      {/each}
      <button on:click={addRow}>add</button>
    </tr>
  {/if}
</table>
