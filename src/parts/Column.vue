<template>
    <div class="col">
        <div class="header">
            <div class="right">
                <img src="../assets/svg/bull.svg" />
                <p>{{ col.heading }}</p>
            </div>
            <div class="left">{{ realLength }}</div>
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
    props: {
        col: {
            type: Object,
            required: true,
        },
        realLength: {
            type: Number,
            required: true,
        },
    },
    components: {
        TodoItem,
    },
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/parts/column.scss";
</style>
