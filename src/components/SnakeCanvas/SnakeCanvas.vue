<template>
    <canvas ref="board" id="snake-canvas" :width="boardSizePx" :height="boardSizePx"></canvas>
</template>

<script>

export default {
    name: "SnakeCanvas",
    props: {
        cellSize: Number,
        boardSize: Number,
        speed: Number
    },
    computed: {
        boardSizePx() {
            return this.cellSize * this.boardSize
        }
    }
}
</script>

<style scoped>
#snake-canvas {
    border: 1px solid #ccc;
    margin: 10px 0;
}
</style>
