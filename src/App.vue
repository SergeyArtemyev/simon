<template>
  <div id="app">
    <h1>Simon Says</h1>
    <Game />
  </div>
</template>

<script>
import Game from './components/Game'

export default {
  name: 'App',
  components: {
    Game
  }
}
</script>

<style>
  body {
    font-family: Arial, Helvetica, sans-serif;
    background: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  h1 {
    text-align: center;
  }
</style>
