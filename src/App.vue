

<template>
 <div>
      <div v-if="startButton">
        <button @click="startButton = !startButton">Start game</button>
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

</style>
