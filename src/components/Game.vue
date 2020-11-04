<template>
  <div class="game-container">
    <GameField :playerGuess="playerGuess" :guess="guess"/>
    <GameControl :startGame="startGame" :answer="answer" :round="round" :difficulty="difficulty" v-on:clicked="changeDifficulty"/>    
  </div>

</template>
<script>
import GameField from './GameField';
import GameControl from './GameControl';

let interval;
let timeout;
let randomBox;
let counter = 0;
let message;
function getDomEl(){
  if(message){
    return message;
  } else {
    return message = document.querySelector('.message');
  }
}
export default {
  name: 'Game',
  components: {
    GameField,
    GameControl
  },
  data(){
    return {
      round: 1,
      answer: [],
      guess: [],
      difficulty: 1500,
      enabled: false
    }
  },
  methods: {
    play(e){
      e.target.firstElementChild.play();
      let prev = this.guess.length;
      this.guess.push(e.target.id);
      timeout = setTimeout(()=> {
        if(this.guess.length === prev || this.guess.length < this.answer.length){
          this.checkGuess();
        } else {
          this.checkGuess();
        }
      }, this.difficulty);
    },
    task(){
      getDomEl().innerHTML = "";
      let boxes = document.querySelectorAll('.box');
      interval = setInterval(()=>{
        if(counter < this.round) {
          randomBox = Math.floor(Math.random() * 4);
          this.answer.push(boxes[randomBox].id);
          boxes[randomBox].firstElementChild.play();
          boxes[randomBox].animate([
            {opacity: '0.5'},
            {opacity: '1'},
          ], {duration: 500})
          counter++;
        } else {
          clearInterval(interval);
        }
      }, 1000)
    },
    playerGuess(e){
      if(this.enabled){
        clearTimeout(timeout)
        this.play(e)
      }
    },
    checkGuess(){
      for(let i = 0; i < this.answer.length; i++){
        if(this.answer[i] !== this.guess[i]){
          getDomEl().innerHTML = `
            <p>Вы проиграли!</p>
            <p>Правильно: ${this.answer.join(', ')}</p>
            <p>Ваш варинат: ${this.guess.join(', ')}</p>
          `;
          this.answer = [];
          this.guess = [];
          this.round = 1;
          counter = 0;
          this.enabled = false;
          return;
        } 
      }
      getDomEl().innerHTML = "Вы победили!"
      counter = 0;
      this.round++;
      this.answer = [];
      this.guess = [];
      this.enabled = false;
    },
    changeDifficulty(value){
      getDomEl().innerHTML = "";
      this.difficulty = value;
      this.answer = [];
      this.guess = [];
      this.round = 1;
      counter = 0;
      this.enabled = false;
    },
    startGame(){
      this.enabled = true;
      this.task();
    }
  }
}
</script>

<style>
  .game-container {
    display: flex;
  }
</style>