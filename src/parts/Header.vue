<template>
    <div class="header">
        <div class="left">
            <div class="leftInner">
                <div class="redSqr">
                    <p>P</p>
                </div>
                <p class="headerTxt">Privacy Credits</p>
            </div>
        </div>
        <div class="right">
            <div class="btns">
                <div class="border" />
                <div class="question">
                    <img src="@/assets/svg/_.svg" alt="" />
                </div>
                <div class="border" />
                <div class="ellipse">
                    <img src="@/assets/svg/Ellipse.svg" alt="" />
                </div>
            </div>
            <div class="createBtn" @click="openModal()">
                <img src="@/assets/svg/Vector.svg" />
                <p>Создать заявку</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    methods: {
        openModal() {
            this.$emit("toggleModal", true)
        },
    },
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/parts/header.scss";
</style>
