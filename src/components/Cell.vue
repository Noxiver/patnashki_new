<template>
    <button class="cell" @click="$emit('move_cell', id_cell)">
        {{value != 0? value : ""}}
    </button>
</template>

<script>
    export default {
        name: 'Cell',
        props: {
            id_cell: Number,
            value: {
                type: Number,
                default: 0
            }
        }
    }
</script>
<style scoped lang="scss">
    .cell {
        box-shadow: 5px 5px 5px #173F5F ;
        outline: none;
        width: 150px;
        height: 150px;
        position: relative;
        border: 1px solid #ed553b;
        background: #3caea3;
        color: #20639b;
        border-radius: 10px;
        text-align:center;
        font-size: 70px;
        cursor: pointer;
        font-family: "Geomanist Thin";
        justify-content: center;

    }

</style>
