<template>
    <div class="loader">
        <div class="inner"></div>
    </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
@keyframes load {
    0% {
        transform: rotate(0deg);
    }
    50% {
        transform: rotate(180deg);
    }
    100% {
        transform: rotate(360deg);
    }
}
.loader {
    > .inner {
        width: 100px;
        height: 100px;
        border: 2px solid white;
        border-radius: 50%;
        border-bottom: none;
        animation: load 2s linear infinite;
    }
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: #000000a0;
    z-index: 100;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
