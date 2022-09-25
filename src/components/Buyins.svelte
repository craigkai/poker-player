<script lang="ts">
  import EditableTable from "./EditableTable.svelte";

  let columns = ["Player", "Buy in"]
  let data = [
    ["John", "20, 40"],
    ["Craig", "20, 20"]
  ]
</script>

<EditableTable {columns} {data} />
