<script>
  export let space = "";
  export let winner;
  $: won = space === winner;
</script>
<style>
  .space{
    border: solid 1px grey;
    height: 125px;
    width: 125px;
    flex:1;
    align-content: center;
    justify-content: center;
    font-size: 75px;
    text-align: center;
    line-height: 125px;
    cursor: pointer;
  }
  .winning{
    color: yellow;
  }
</style>

<div class:winning={won} on:click class="space">{space}</div>