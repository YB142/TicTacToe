<template>
  <div>
   <div v-if="quitButton">
      <div>
      <h1>TicTacToe</h1>
      <p>Rules: In order to win you must have 3 tokens either in a row, column, or diagonally.</p>
      <div v-if="tokenPicked">
        <h2>Pick your token</h2>
      <ul @click="tokenPicked = !tokenPicked" id="tokenbutton"><button id="tokenX">X</button><button id="tokenO">O</button></ul>
      </div>
      </div>
      <ul id="gameboard">
        <div class="rows" id="row1">
          <button class="buttons" id="button1"></button>
          <button class="buttons" id="button2"></button>
          <button class="buttons" id="button3"></button>
        </div>
        <div class="rows" id="row2">
          <button class="buttons" id="button4"></button>
          <button class="buttons" id="button5"></button>
          <button class="buttons" id="button6"></button>
        </div>
        <div class="rows" id="row3">
          <button class="buttons" id="button7"></button>
          <button class="buttons" id="button8"></button>
          <button class="buttons" id="button9"></button>
        </div>
      </ul>
      <footer>
        <button @click="quitButton = !quitButton">Quit Game</button>
      </footer>
    </div>
    <quitScreen v-else></quitScreen>
  </div>
</template>

<script>
import quitScreen from "./quitScreen.vue";
export default {
  components: {
    quitScreen
  },
  data() {
    return {
      quitButton: true,
      tokenPicked: true
    }
  }
}
</script>

<style>
    .buttons {
        padding: 100px;
    }
    #gameboard {
      margin-left: 475px;
      margin-top: 20px;
    }
    h1 {
      text-align: center;
      font-size: 50px;
    }
    p {
      font-size: 30px;
      text-align: center;
    }
    footer {
      margin-top: 30px;
      text-align: center;
    }
    h2 {
      text-align: center;
    }
    #tokenbutton {
      margin-left: 750px;
    }

</style>