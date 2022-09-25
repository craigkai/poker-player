<script lang="ts">
  import EditableTable from "./EditableTable.svelte";

  let columns = ["20", "30", "40"];
  let show_rows=false;
</script>

Blinds:
<EditableTable {columns} {show_rows} />
