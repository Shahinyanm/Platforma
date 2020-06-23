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
                    <img src="../assets/_.svg" alt="" />
                </div>
                <div class="border" />
                <div class="ellipse">
                    <img src="../assets/Ellipse.svg" alt="" />
                </div>
            </div>
            <div class="createBtn" @click="openModal()">
                <img src="../assets/Vector.svg" />
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ellipse > img {
    margin: 0 18px;
}
.createBtn:hover {
    background-color: #006aff;
    cursor: pointer;
}
.ellipse {
    display: flex;
    align-items: center;
}
.question {
    padding: 0 20.08px;
}
.border {
    opacity: 0.2;
    /* Gray */
    width: 0;
    border-right: 1px solid #7d8790;
    /* transform: rotate(90deg); */
    height: 100%;
}
.btns {
    /* background-color: yellow; */
    height: 40px;
    /* width: 50px; */
    display: flex;
    align-items: center;
}
.createBtn > img {
    margin-right: 8.85px;
}
.createBtn > p {
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    color: #ffffff;
}
.right {
    height: 100%;
    display: flex;
    align-items: center;
}
.createBtn {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 17px 0 15.85px;
    background: #398bff;
    /* padding: 17px; */
    height: 100%;
}
.header {
    z-index: 10;
    background-color: #2a3247;
    position: sticky;
    left: 0;
    width: 100%;
    display: flex;
    align-items: center;
    /* padding-left: 70px; */
    height: 50px;

    justify-content: space-between;
}
.redSqr > p {
    font-family: monospace;
    font-style: normal;
    font-weight: bold;
    font-size: 11px;
    line-height: 13px;
    /* identical to box height */

    display: flex;
    align-items: center;
    text-align: center;

    /* #FFFFFF */

    color: #ffffff;
}
.leftInner {
    display: flex;
}
.redSqr {
    display: inline-block;
    background-color: #f24651;
    border-radius: 2px;
    width: 16px;
    margin-left: 70px;
    min-width: 16px;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 16px;
}
.headerTxt {
    margin-left: 5px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 14px;
    /* identical to box height, or 100% */

    display: flex;
    align-items: center;

    /* #FFFFFF */

    color: #ffffff;
}
</style>
