<template>
  <div class='border'>
    <div class="game-field">
      <div v-on:click="playerGuess" id="blue" class="box"><audio src="../assets/sounds/1.mp3"></audio></div>
      <div v-on:click="playerGuess" id="red" class="box"><audio src="../assets/sounds/2.mp3"></audio></div>
      <div v-on:click="playerGuess" id="yellow" class="box"><audio src="../assets/sounds/3.mp3"></audio></div>
      <div v-on:click="playerGuess" id="green" class="box"><audio src="../assets/sounds/4.mp3"></audio></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GameField',
  props: ["playerGuess"]
}
</script>

<style>
  .border {
    background: #222;
    width: 315px;
    height: 315px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .game-field {
    position: absolute;
    width: 300px;
    height: 300px;
    display: flex;
    flex-wrap: wrap;
    border-radius: 50%;
    overflow: hidden;
  }
  .box {
    flex: 0 0 50%;
    height: 50%;
    cursor: pointer;
  }

  .box:hover {
    opacity: 1 !important;
  }

  #blue {
    background: #0000ff;
    opacity: 0.5;
  }
  #red {
    background: #ff0000;
    opacity: 0.5;
  }
  #yellow {
    background: #ffff00;
    opacity: 0.5;
  }
  #green {
    background: #008000;
    opacity: 0.5;
  }
</style>