<template>
  <div>
   <div v-if="quitButton">
      <div>
      <h1>TicTacToe</h1>
      <p>Rules: In order to win you must have 3 tokens either in a row, column, or diagonally.</p>
      <div v-if="tokenPicked">
        <h2>Pick your token</h2>
      <ul @click="tokenPicked = !tokenPicked" id="tokenbutton"><button @click="token = 'X'" id="tokenX">X</button><button @click="token = 'O'" id="tokenO">O</button></ul>
      </div>
      </div>
      <ul id="gameboard">
        <div class="rows" id="row1">
          <button @click="button1 = token" class="buttons" >{{button1}}</button>
          <button @click="button2 = token" class="buttons" >{{button2}}</button>
          <button @click="button3 = token" class="buttons" >{{button3}}</button>
        </div>
        <div class="rows" id="row2">
          <button @click="button4 = token" class="buttons" >{{button4}}</button>
          <button @click="button5 = token" class="buttons" >{{button5}}</button>
          <button @click="button6 = token" class="buttons" >{{button6}}</button>
        </div>
        <div class="rows" id="row3">
          <button @click="button7 = token" class="buttons" >{{button7}}</button>
          <button @click="button8 = token" class="buttons" >{{button8}}</button>
          <button @click="button9 = token" class="buttons" >{{button9}}</button>
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
      tokenPicked: true,
      token: "",
      button1: "",
      button2: "",
      button3: "",
      button4: "",
      button5: "",
      button6: "",
      button7: "",
      button8: "",
      button9: ""
    }
  }
}
</script>

<style>
    .rows {
      max-height: 100px;
    }
    .buttons {
        width: 100px;
        height: 100px;
        font-size: 50px;
        background-color: black;
        color: white;
        border: 2px solid white;
        vertical-align: middle;
    }
    #gameboard {
      margin-left: 625px;
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