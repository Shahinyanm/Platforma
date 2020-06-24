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
            <img v-else src="@/assets/svg/VectorR.svg" />
        </div>
        <div class="bottom" :style="{ color: detail.valueColor }">
            {{ detail.value }}
        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        detail: {
            type: Object,
            required: true,
        },
    },
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/components/card.scss";
</style>
