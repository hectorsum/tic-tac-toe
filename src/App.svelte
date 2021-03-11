<script>
  import Space from './Space.svelte';
  import gameStore from './game-store';
  let board = ['', '', '', '', '', '', '', '', '', '', ''];
  let nextPlayer = '';
  let winner;
  let numberOfPeeps = 0;
  gameStore.subscribe((data) => {
    if (!data) {
      return;
    }
    winner = data.winner;
    nextPlayer = data.nextPlayer;
    board = data.board;
    numberOfPeeps = data.numberOfPeeps;
  });
</script>

<main>
  <h1>Tic Tac Toe</h1>
  <h2>Number of people playing: {numberOfPeeps}</h2>
  {#if winner == 'TIE'}
    <h2>Tie Game!!</h2>
  {:else}
    <h2>Player {winner} won!!</h2>
  {/if}
  <h2>Player X</h2>
  <div class="row">
    <Space space={board[0]} />
    <Space space={board[1]} />
    <Space space={board[2]} />
  </div>
  <div class="row">
    <Space space={board[3]} />
    <Space space={board[4]} />
    <Space space={board[5]} />
  </div>
  <div class="row">
    <Space space={board[6]} />
    <Space space={board[7]} />
    <Space space={board[8]} />
  </div>
  {#if winner}
    <button> New Game </button>
  {/if}
</main>

<style>
  main {
    width: 475px;
    margin: 0 auto;
    border: black solid;
    height: 1000px;
  }
  .row {
    display: flex;
  }
  button {
    width: 100%;
    margin-top: 20px;
    border-radius: 0;
    background-color: lightblue;
    font-size: 30px;
    cursor: pointer;
    border: none;
    outline: none;
  }
  button:hover {
    outline: none;
  }
</style>
