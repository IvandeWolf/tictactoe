<template>
  <div class="w-screen h-screen bg-gray-50 flex flex-col justify-center items-center overflow-auto">
    <h2 class="text-6xl mb-8">Turn: {{ activePlayer }}</h2>

    <!-- Total board -->
    <div class="grid grid-cols-3 grid-rows-3">
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4 border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 0" :board="boards[0]" v-on:cellClicked="handleClick(0, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4 border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 1" :board="boards[1]" v-on:cellClicked="handleClick(1, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 2" :board="boards[2]" v-on:cellClicked="handleClick(2, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4 border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 3" :board="boards[3]" v-on:cellClicked="handleClick(3, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4 border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 4" :board="boards[4]" v-on:cellClicked="handleClick(4, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-b-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 5" :board="boards[5]" v-on:cellClicked="handleClick(5, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 6" :board="boards[6]" v-on:cellClicked="handleClick(6, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center border-r-4">
        <TicTacToe :active="activeBoard === null || activeBoard === 7" :board="boards[7]" v-on:cellClicked="handleClick(7, $event)" :activePlayer="activePlayer" />
      </div>
      <div class="w-32 h-32 lg:w-64 lg:h-64 flex justify-center items-center">
        <TicTacToe :active="activeBoard === null || activeBoard === 8" :board="boards[8]" v-on:cellClicked="handleClick(8, $event)" :activePlayer="activePlayer" />
      </div>
    </div>
  </div>
</template>

<script>
import TicTacToe from '@/components/TicTacToe'

export default {
  name: 'Home',
  components: { TicTacToe },
  data: () => ({
    boards: [],
    activeBoard: null,
    activePlayer: 'X'
  }),
  mounted () {
    this.boards = [
      null, null, null,
      null, null, null,
      null, null, null
    ]

    for (let i = 0; i < 9; i++) {
      this.boards[i] = [
        null, null, null,
        null, null, null,
        null, null, null
      ]
    }
  },
  methods: {
    handleClick (boardIndex, cellIndex) {
      const board = this.boards[boardIndex]

      if (board[cellIndex]) return

      board[cellIndex] = this.activePlayer
      this.activePlayer = this.activePlayer === 'X' ? 'O' : 'X'

      this.activeBoard = cellIndex

      this.checkWin(board)
    }
  }
}
</script>
