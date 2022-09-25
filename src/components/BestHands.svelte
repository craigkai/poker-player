<script lang="ts">
  import EditableTable from "./EditableTable.svelte";

  let columns = ["Best Hands"]
  let data = [
    ["3 3"],
  ]
</script>

<EditableTable {columns} {data} />
