<script lang="ts">
  let squares: string[] = Array(9).fill("");
  let isX = true;
  function onClick(i: number) {
    if (squares[i] !== "") return;
    squares[i] = isX ? "X" : "O";
    squares = squares;
    isX = !isX;
  }
</script>

<div class="container">
  {#each squares as square, i}
    <button on:click={() => onClick(i)}>{square}</button>
  {/each}
</div>

<style>
  * {
    box-sizing: border-box;
  }

  :global(body) {
    font-family: sans-serif;
    margin: 20px;
    padding: 0;
  }

  button {
    background: #fff;
    border: 1px solid #999;
    float: left;
    font-size: 24px;
    font-weight: bold;
    line-height: 34px;
    height: 68px;
    margin-right: -1px;
    margin-top: -1px;
    padding: 0;
    text-align: center;
    width: 68px;
  }

  .container {
    width: 204px;
    display: flex;
    flex-wrap: wrap;
  }
  .container > button {
    flex: 1 0 31%;
  }
</style>
