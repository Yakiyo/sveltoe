<script lang="ts">
  let squares: string[] = Array(9).fill("");
  let isX = true;
  let winner: string | null = null;
  let isStalemate = false;
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  function onClick(i: number) {
    if (winner) return;
    if (squares[i] !== "") return;
    squares[i] = isX ? "X" : "O";
    squares = squares;
    isX = !isX;
    winner = calculateWinner(squares);
    isStalemate = calculateStalemate(squares);
  }

  function calculateStalemate(squares: string[]) {
    return !squares.some((x) => x === '') && !winner;
  }

  function calculateWinner(squares: string[]) {
    for (let i = 0; i < lines.length; i++) {
      const [a, b, c] = lines[i];
      if (
        squares[a] &&
        squares[a] === squares[b] &&
        squares[a] === squares[c]
      ) {
        return squares[a];
      }
    }
    return null;
  }
</script>

<h1>Tic Tac Toe</h1>

<div class="container">
  {#each squares as square, i}
    <button class="square" on:click={() => onClick(i)}>{square}</button>
  {/each}
</div>

<h2>
  {#if winner}
    Winner is player {winner}
  {:else if isStalemate}
    Match is over without any winner. Restart to play again.
  {:else}
    Current player: {isX ? "X" : "O"}
  {/if}
</h2>
<button on:click={() => {
  squares = Array(9).fill("");
  isX = true;
  winner = null;
}}>Restart</button>

<style>
  * {
    box-sizing: border-box;
  }

  :global(body) {
    font-family: sans-serif;
    margin: 20px;
    padding: 0;
  }

  .square {
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
