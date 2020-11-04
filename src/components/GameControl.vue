<template>
  <div class="controls">
    <h2 class="round">
      Раунд: {{round}}
    </h2>
    <p>Нажми старт, чтобы начать новый раунд</p>
    <button v-on:click="startGame">Старт</button>
    <!-- Message -->
    <p class="message"></p>
    <!-- Options -->
    <div class="game-options">
      <h3>Уровнь сложности</h3>
      <label for="easy">
        <input type="radio" @click="$emit('clicked', 1500)" name="difficulty" id="easy" checked>
        Легкий (1.5 секунд)
      </label>
      <label for="normal">
        <input type="radio" @click="$emit('clicked', 1000)" name="difficulty" id="normal">
        Средний (1 секунда)
      </label>
      <label for="hard">
        <input type="radio" @click="$emit('clicked', 400)" name="difficulty" id="hard">
        Трудный (0.4 секунды)
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GameControl',
  props: ["startGame", "round"],
}
</script>

<style>
  .controls {
    margin-left: 2rem;
  }

  button {
    font-size: 1.2rem;
    padding: 0.9rem 1.5rem;
    border: 0;
    background: #add8e6;
    border-radius: 15px;
    cursor: pointer;
  }

  button:hover {
    background: #afdeee;
  }

  button:focus {
    outline: 0;
  }

  .game-options {
    display: flex;
    flex-direction: column;
  }

  h3 {
    margin-bottom: 0.5rem;
  }

  label {
    margin: 0.5rem 0;
  }
</style>