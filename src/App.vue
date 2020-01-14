<template>
    <div id="app">
        <div class="wrap">
            <div id="attemptСounter">
                <h1>Ходов: {{counter}}</h1>
            </div>
            <div class="gameBox">
                <Cell
                        v-for="(cell, index) in cells"
                        :value="cell"
                        :id_cell="index"
                        :key="index"
                        @move_cell="moveCell"
                ></Cell>
            </div>
        </div>
    </div>
</template>

<script>
    //es-lint disable
    import Cell from "./components/Cell.vue";

    export default {
        name: "app",
        components: {
            Cell
        },
        created() {
            return this.shuffle(this.cells);
        },
        data() {
            return {
                cells: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 0],
                model: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 0],
                counter: 0
            };
        },

        methods: {

            shuffle(a) {
                for (let i = a.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [a[i], a[j]] = [a[j], a[i]];
                }
                return a;
            },
            checkArray() {
                // this.cells === this.cells.sort((a, b) => (a * b == 0 ? b - a : a - b))
                let result = 0;
                for (let index = 0; index < this.model.length; index++) {
                    if (this.model[index] == this.cells[index]) result++;
                }
                if (result > 15) alert("вы победили!");
            },
            moveCell(index) {
                // alert(index);
                let valueCell = this.cells[index];

                if (this.cells[index - 1] == 0) {
                    this.cells[index] = 0;
                    this.cells[index - 1] = valueCell;
                    this.counter++
                } else if (this.cells[index - 4] == 0) {
                    this.cells[index] = 0;
                    this.cells[index - 4] = valueCell;
                    this.counter++
                } else if (this.cells[index + 1] == 0) {
                    this.cells[index] = 0;
                    this.cells[index + 1] = valueCell;
                    this.counter++
                } else if (this.cells[index + 4] == 0) {
                    this.cells[index] = 0;
                    this.cells[index + 4] = valueCell;
                    this.counter++
                }
                this.checkArray();
            }
        }
    };
</script>

<style lang="scss">
    body {
        background-color: #f6d55c;

        #app {
            width: fit-content;
            height: fit-content;
            margin: auto;
            background-color: #f6d55c;
            .wrap {
                width: fit-content;
                height: fit-content;

                #attemptСounter {
                    margin: auto;
                    width: fit-content;
                    h1{
                        font-family: "Century Gothic" ;
                    }
                }
                .gameBox {
                    display: grid;
                    grid-template-rows: 1fr 1fr 1fr;
                    grid-template-columns: 1fr 1fr 1fr 1fr;
                    grid-gap: 10px;
                    width: fit-content;
                    height: fit-content;
                    padding: 5px;
                }
            }
        }
    }
</style>
<!--
  position: absolute;
  left: 50%;
  transform: translate(0, 50%);
  margin: 0;
  padding: 0;-->
