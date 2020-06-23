<template>
    <div class="card">
        <div class="top">
            <p class="left" :style="{ color: detail.leftTextColor }">
                {{ detail.leftText }}
            </p>
            <p
                v-if="!detail.isSymbol"
                class="right"
                :style="{ color: detail.rightTextColor }"
            >
                {{ detail.rightTxt }}
            </p>
            <img v-else src="../assets/VectorR.svg" />
        </div>
        <div class="bottom" :style="{ color: detail.valueColor }">
            {{ detail.value }}
        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: ["detail"],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card:hover {
    cursor: pointer;
    box-shadow: 0 0 5px black;
}
.top > img {
    margin: 6px 4px 0 0;
}
.right {
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 14px;
}
.left {
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 14px;
}
.card {
    width: 180px;
    min-width: 166px;
    margin: 0 5px;
    background-color: #ffffff;
    border-radius: 5px;
    padding: 7px;
}
.top {
    display: flex;
    margin-bottom: 7px;
    justify-content: space-between;
}
.bottom {
    display: flex;
    flex-direction: row-reverse;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 24px;
    line-height: 28px;
}
</style>
