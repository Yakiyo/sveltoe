<script lang="ts">
  const squares: string[] = Array(9).fill("");
  let isX = true;
  function onClick(i: number) {
    if (squares[i] !== "") return;
    squares[i] = isX ? "X" : "O";
    isX = !isX;
  }
</script>

<div>
  {#each squares as square, i}
    <button class="border-solid border-8 border-gray-500 w-20 h-20"
      >{square}</button
    >
  {/each}
</div>
