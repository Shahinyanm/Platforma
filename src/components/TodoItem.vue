<template>
    <div class="item">
        <div class="header">
            <p class="name">{{ item.heading }}</p>
            <p class="time">{{ item.time }}</p>
        </div>
        <div class="itemBodyCon">
            <p class="itemBody">
                {{ item.text }}
            </p>
        </div>
        <div class="footer">
            <div class="state">{{ item.state }}</div>
            <div class="day">
                <span>{{ item.day }}</span>
                <img src="../assets/svg/gDot.svg" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/components/todoItem.scss";
</style>
