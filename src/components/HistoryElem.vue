<template>
    <div class="outer">
        <div class="heading">
            <span>{{ time }}</span>
            <span class="headingLabel">{{ label }}</span>
        </div>
        <slot></slot>
    </div>
</template>

<script>
export default {
    nane: "HistoryElem",
    props: ["label", "time"],
}
</script>

<style scoped lang="scss">
.heading {
    margin-bottom: 7px;
    display: flex;
    align-items: center;
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 12px;
    display: flex;
    align-items: center;
    color: #7d8790;
    > .headingLabel {
        margin-left: 9px;
        font-weight: 500;
    }
}
</style>
