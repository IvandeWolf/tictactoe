<template>
  <div v-if="board" class="relative grid grid-cols-3 grid-rows-3" :class="active ? '' : 'opacity-20'">
    <Cell v-for="(cell, index) in board" :key="index" :cell="cell" :index="index" :active="active" :activePlayer="activePlayer" @cellClicked="handleClick(index)" />

    <!-- Drawing lines -->
    <div class="absolute w-full h-full pointer-events-none">
      <!-- \ -->
      <svg v-if="checkWin(0, 4, 8)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="2" y1="2" x2="22" y2="22" stroke-width=".6" />
      </svg>
      <!-- / -->
      <svg v-if="checkWin(2, 4, 6)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="22" y1="2" x2="2" y2="22" stroke-width=".6" />
      </svg>
      <!-- | -->
      <svg v-if="checkWin(0, 3, 6)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="4" y1="2" x2="4" y2="22" stroke-width=".6" />
      </svg>
      <!-- | -->
      <svg v-if="checkWin(1, 4, 7)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="12" y1="2" x2="12" y2="22" stroke-width=".6" />
      </svg>
      <!-- | -->
      <svg v-if="checkWin(2, 5, 8)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="20" y1="2" x2="20" y2="22" stroke-width=".6" />
      </svg>
      <!-- - -->
      <svg v-if="checkWin(0, 1, 2)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="2" y1="4" x2="22" y2="4" stroke-width=".6" />
      </svg>
      <!-- - -->
      <svg v-if="checkWin(3, 4, 5)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="2" y1="12" x2="22" y2="12" stroke-width=".6" />
      </svg>
      <!-- - -->
      <svg v-if="checkWin(6, 7, 8)" class="absolute w-full h-full text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <line x1="2" y1="20" x2="22" y2="20" stroke-width=".6" />
      </svg>
    </div>
  </div>
</template>

<script>
import Cell from '@/components/Cell'

export default {
  name: 'TicTacToe',
  components: { Cell },
  props: {
    active: Boolean,
    board: Array,
    activePlayer: String
  },
  methods: {
    handleClick(index) {
      this.$emit('cellClicked', index)
    },
    checkWin(a, b, c) {
      return this.board[a] && this.board[a] === this.board[b] && this.board[a] === this.board[c]
    }
  }
}
</script>
