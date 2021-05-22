<template>
    <canvas ref="board" id="snake-canvas" :width="boardSizePx" :height="boardSizePx"></canvas>
</template>

<script>

export default {
    name: "SnakeCanvas",
    props: {
        cellSize: Number,
        boardSize: Number,
        speed: Number,
        isPlaying: Boolean
    },
    computed: {
        boardSizePx() {
            return this.cellSize * this.boardSize
        }
    },
    mounted() {
        this.boardContext = this.$$refs.board.getContext('2d');
    },
    created() {
        this.resetSnake(); // once the component is rendered
    },
    watch: {
        isPlaying(value) {
            if (value) {
                this.resetSnake();
                this.move();
            }
        }
    },
    methods: {
        resetSnake() {
            this.snake = [
                {
                    x: this.getMiddleCell(),
                    y: this.getMiddleCell()
                }
            ]
        },
        getMiddleCell() {
            return Math.round(this.boardSize / 2); // It means the snake will always begin right in the middle
        },
        move() {
            this.snake.forEach(this.drawCell);
        },
        drawCell({ x, y }) {
            this.boardContext.rect(
                x * this.cellSize,
                y * this.cellSize,
                this.cellSize,
                this.cellSize
            );
            this.boardContext.fillStyle = "black";
            this.boardContext.fill(); // draws one specific cell
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
