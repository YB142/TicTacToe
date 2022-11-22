<template>
  <div>
    <div>
      <div v-if="quitButton">
      <div>
        <h1>TicTacToe</h1>
        <div id="winningText">
          <h2 v-if="firstRowWin()">1st row Winner</h2>
          <h3 v-if="secondRowWin()">2nd row Winner</h3>
          <h4 v-if="thirdRowWin()">3rd row Winner</h4>
          <h5 v-if="firstColumnWin()">1st column Winner</h5>
          <h6 v-if="secondColumnWin()">2nd column Winner</h6>
          <h7 v-if="thirdColumnWin()">3rd column Winner</h7>
          <h8 v-if="leftDiagnoWin()">Left diagno Winner</h8>
          <h9 v-if="rightDiagnoWin()">Right diagno Winner</h9>
          <h10 v-if="draw()">Draw</h10>
        </div>
        <div v-if="!winner">
          <p>Rules: In order to win you must have 3 tokens either in a row, column, or diagonally.</p>
          <div v-if="!tokenPicked">
            <h2>Click to pick starting token</h2>
            <ul @click="tokenPicked = !tokenPicked" id="tokenbutton">
              <button @click="tokenO" id="tokenO">X</button>
              <button @click="tokenX" id="tokenX">O</button>
            </ul>
          </div>
        <!-- v-for="item in array" -->
        <table id="GB" >
          <tr v-for="(row, r) in rows" :key="r" class="rows">
            <td @click="onCellClick(r,c)" v-for="(cell, c) in row" :key="c" class="td"> {{ cell }} </td>
          </tr>
        </table>
        </div>
      </div>
      <footer>
        <div>
          <button @click="quitButton = !quitButton">Quit Game</button>
          <form>
            <button>Restart Game</button>
          </form>
        </div>
      </footer>
      </div>
      <quitScreen v-else></quitScreen>
    </div>
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
      tokenPicked: false,
      token: "",
      rows: [
        ["", "", ""], 
        ["", "", ""], 
        ["", "", ""]
      ],
      otherToken: "",
      empty: "",
      winner: false
    }
  },
  methods: {
    onCellClick(r,c) {
      [this.token, this.otherToken] = [this.otherToken, this.token]
      this.$set(this.rows[r], c, this.token);
    },
    tokenX() {
      this.token = "X";
      this.otherToken = "O"
    },
    tokenO() {
      this.token = "O";
      this.otherToken = "X"
    },
    firstRowWin() {
      for (const cell of this.rows[0]) {
        if (cell === "" || cell === this.otherToken) {
          return false;
        } 
      }
      this.winner = true;
      return true;
    },
    secondRowWin() {
      for (const cell of this.rows[1]) {
        if (cell === "" || cell === this.otherToken) {
          return false;
        }
      }
      this.winner = true;
      return true;
    },
    thirdRowWin() {
      for (const cell of this.rows[2]) {
        if (cell === "" || cell === this.otherToken) {
          return false;
        }
      }
      this.winner = true;
      return true;
    },
    firstColumnWin() {
      for (const cell of this.rows) {
        if (cell[0] === "" || cell[0] === this.otherToken) {
          return false;
        }
      }
      this.winner = true;
      return true;
    },
    secondColumnWin() {
      for (const cell of this.rows) {
        if (cell[1] === "" || cell[1] === this.otherToken) {
          return false;
        }
      }
      this.winner = true;
      return true;
    },
    thirdColumnWin() {
      for (const cell of this.rows) {
        if (cell[2] === "" || cell[2] === this.otherToken) {
          return false;
        }
      }
      this.winner = true;
      return true;
    },
    leftDiagnoWin() {
      for (const row of this.rows) {
        if (this.rows[0][0] === "" || this.rows[0][0] === this.otherToken) {
          return false;
        }
        if (this.rows[1][1] === "" || this.rows[1][1] === this.otherToken) {
          return false;
        }
        if (this.rows[2][2] === "" || this.rows[2][2] === this.otherToken) {
          return false;
        }
        this.winner = true;
        return true;
      }
    },
    rightDiagnoWin() {
      for (const row of this.rows) {
        if (this.rows[0][2] === "" || this.rows[0][2] === this.otherToken) {
          return false;
        }
        if (this.rows[1][1] === "" || this.rows[1][1] === this.otherToken) {
          return false;
        }
        if (this.rows[2][0] === "" || this.rows[2][0] === this.otherToken) {
          return false;
        }
        this.winner = true;
        return true;
      }
    },
    draw() {
      if (this.rows[0][0] != "") {
        if (this.rows[0][1] != "") {
          if (this.rows[0][2] != "") {
            if (this.rows[1][0] != "") {
              if (this.rows[1][1] != "") {
                if (this.rows[1][2] != "") {
                  if (this.rows[2][0] != "") {
                    if (this.rows[2][1] != "") {
                      if (this.rows[2][2] != "") {
                        this.winner = true
                        return true;
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
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
  text-align: center;
  font-family: cursive;
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

#winningText {
  text-align: center;
  font-family: cursive;
  font-size: large;
}


</style>