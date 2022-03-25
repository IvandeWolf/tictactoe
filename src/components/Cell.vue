<template>
  <div @click="handleClick(index)" class="w-10 h-10 lg:w-20 lg:h-20 flex justify-center items-center" :class="[active || cell ? 'cursor-pointer hover:bg-gray-100' : 'cursor-not-allowed', index < 6 ? 'border-b-2' : '', index % 3 !== 2 ? 'border-r-2' : '']">
    <Cross
      v-if="cell === 'X'"
    />
    <Circle
      v-else-if="cell === 'O'"
    />
    <div v-else>&nbsp;</div>
  </div>
</template>

<script>
import Cross from '@/components/Cross'
import Circle from '@/components/Circle'

export default {
  name: 'Cell',
  components: { Cross, Circle },
  props: {
    board: Array,
    cell: String,
    index: Number,
    active: Boolean,
    activePlayer: String
  },
  methods: {
    handleClick(index) {
      if (!this.active) return

      this.$emit('cellClicked', index)
    }
  }
}
</script>
