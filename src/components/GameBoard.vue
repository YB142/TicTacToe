<template>
  <div>
    <div v-if="quitButton">
      <div>
        <h1>TicTacToe</h1>
        <p>Rules: In order to win you must have 3 tokens either in a row, column, or diagonally.</p>
        <div v-if="tokenPicked">
          <h2>Pick your token</h2>
          <ul @click="tokenPicked = !tokenPicked" id="tokenbutton"><button @click="token = 'X'"
              id="tokenX">X</button><button @click="token = 'O'" id="tokenO">O</button></ul>
        </div>
        <!-- v-for="name in array" -->
        <table id="GB">
          <tr v-for="(row, r) in rows" :key="r" class="rows">
            <td @click="onCellClick(r,c)" v-for="(cell, c) in row" :key="c" class="td"> {{ cell }} </td>


            <!-- <td class="td"> {{row[1]}} </td>
          <td class="td"> {{row[2]}} </td> -->
          </tr>
        </table>

      </div>
      <footer>
        <button @click="quitButton = !quitButton">Quit Game</button>
      </footer>
    </div>
    <quitScreen v-else></quitScreen>
  </div>
</template>

<script>
import quitScreen from "./quitScreen.vue";
import winningScreen from "./winningScreen.vue"
export default {
  components: {
    quitScreen,
    winningScreen
  },
  data() {
    return {
      quitButton: true,
      tokenPicked: true,
      token: "",
      rows: [
        ["1", "2", "3"], ["4", "5", "6"], ["7", "8", "9"]
      ],
      winner: false
    }
  },
  methods: {
    onCellClick(r,c) {
      console.log("cell clicked", r,c)
      this.$set(this.rows[r], c, this.token);
    }
  }
}
</script>

<style>
.rows {
  max-height: 100px;
}

.td {
  width: 100px;
  height: 100px;
  font-size: 50px;
  background-color: black;
  color: white;
  border: 2px solid white;
  vertical-align: middle;
}

#GB {
  margin-left: 650px;
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