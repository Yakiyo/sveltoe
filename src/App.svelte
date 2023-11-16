<script lang="ts">
  import { writable, type Writable } from "svelte/store";
  const squares: (string)[] = Array(9).fill('');
</script>

{#each squares as square, i}
  <button>{square}</button>
{/each}
