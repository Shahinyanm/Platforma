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
                <img src="../assets/gDot.svg" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["item"],
}
</script>

<style scoped>
.footer > .day {
    display: flex;
    align-items: center;
}
.footer > .day > span {
    margin-right: 2px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 14px;
    text-align: right;

    color: #0abba5;
}
.footer > .state {
    border: 1px solid #e9edf2;
    border-radius: 3px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 14px;
    /* identical to box height */

    display: flex;
    align-items: center;

    /* Gray */

    color: #7d8790;
    padding: 1px 3px 1px 4px;
}
.footer {
    margin-top: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.itemBodyCon {
    padding-right: 13px;
    /* width: 100%; */
    display: -webkit-box;
    overflow: hidden;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
}
.item .itemBody {
    width: 100%;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 17px;
    /* identical to box height */

    color: #35383d;
}
.header {
    display: flex;
    justify-content: space-between;
}
.header > .name {
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 17px;

    /* Gray */

    color: #7d8790;
}
.header > .time {
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 14px;
    text-align: right;

    /* Gray */

    color: #7d8790;
}
.item {
    /* #FFFFFF */

    background: #ffffff;
    /* Light Gray */
    margin: 2.5px 0;
    border: 1px solid #e9edf2;
    border-radius: 5px;
    padding: 5px 5px 8px;
}
.item:hover {
    cursor: pointer;
    box-shadow: 0 0 5px black;
}
</style>
