

<template>
 <div>
      <div v-if="startButton">
        <button id="startB" @click="startButton = !startButton">Start game</button>
      </div>
      <GameBoard v-else></GameBoard>
  </div>

</template>
<script>
import GameBoard from './components/GameBoard.vue';
export default {
  components: {
    GameBoard
  },
  data() {
    return {
      startButton: true
    }
  }
}
</script>
<style>
  #startB {
    padding: 200px;
    font-size: 100px;
    margin-left: 370px;
    margin-top: 185px;
  }
</style>
