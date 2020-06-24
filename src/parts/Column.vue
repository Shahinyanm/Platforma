<template>
    <div class="col">
        <div class="header">
            <div class="right">
                <img src="../assets/bull.svg" />
                <p>{{ col.heading }}</p>
            </div>
            <div class="left">{{ col.number }}</div>
        </div>
        <div class="underline"></div>
        <div class="todoItems">
            <TodoItem
                v-for="(item, index) in col.cards"
                :item="item"
                :key="index"
            />
        </div>
    </div>
</template>

<script>
import TodoItem from "../components/TodoItem"
export default {
    name: "Column",
    props: ["col"],
    components: {
        TodoItem,
    },
}
</script>

<style scoped lang="scss">
.todoItems {
    display: flex;
    flex-direction: column;
}
.left {
    color: #d2d8de;
}
.col {
    padding: 0 10px 2.5px;
    width: 280px;
    min-width: 280px;
}
.underline {
    margin-bottom: 7.5px;
    background: #d2d8de;
    height: 2px;
    width: 100%;
    border-radius: 3px;
}
.header {
    display: flex;
    justify-content: space-between;
    > .right {
        display: flex;
        align-items: center;
        > img {
            margin-right: 7px;
        }
        > p {
            font-family: monospace;
            font-style: normal;
            font-weight: normal;
            font-size: 14px;
            line-height: 17px;
            color: #7d8790;
        }
    }
}
</style>
