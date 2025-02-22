
<script setup>
import { ref } from 'vue';

// Choices for the game
const choices = ["Rock", "Paper", "Scissors"];

// define the playerChoice, computerChoice, and result refs
const playerChoice = ref('');
const computerChoice = ref('');
const result = ref('');

// Function to play the game when a choice button is clicked
const playGame = (choice) => {
  playerChoice.value = choice;
  computerChoice.value = choices[Math.floor(Math.random() * 3)];
  determineWinner();
};

const determineWinner = () => {
  if (playerChoice.value === computerChoice.value) {
    result.value = "It's a Tie!";
  } else if (
    (playerChoice.value === 'Rock' && computerChoice.value === 'Scissors') ||
    (playerChoice.value === 'Scissors' && computerChoice.value === 'Paper') ||
    (playerChoice.value === 'Paper' && computerChoice.value === 'Rock')
  ) {
    result.value = "You Win!";
  } else {
    result.value = "You Lose!";
  }
};
</script>

<template>
  <div class="game-container">
    <h1>Rock, Paper, Scissors Game</h1>
    <div class="choices">
      <button v-for="choice in choices" :key="choice" @click="playGame(choice)">
        {{ choice }}
      </button>
    </div>
    <div class="result">
      <p>Player Choice: <span class="choice-text"> <strong>{{ playerChoice || 'None' }}</strong> </span></p>
      <p>Computer Choice: <span class="choice-text"> <strong>{{ computerChoice || 'None' }}</strong> </span></p>
      <p class="outcome">{{ result }}</p>
    </div>
  </div>
</template>


<style>
.game-container {
  text-align: center;
  font-family: Arial, sans-serif;
}
.choices button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: rgb(244, 242, 157);
}
.choice-text {

font-weight: bold;

}
.result p {
  font-size: 20px;
  background-color: rgb(131, 235, 200);
}
.outcome {
  font-weight: bold;
  font-size: 24px;
}
</style>
