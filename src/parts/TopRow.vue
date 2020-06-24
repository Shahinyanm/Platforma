<template>
    <div class="row">
        <Card v-for="(detail, index) in topRow" :detail="detail" :key="index" />
    </div>
</template>

<script>
import Card from "../components/Card"
export default {
    name: "TopRow",
    props: {
        topRow: {
            type: Array,
            required: true,
        },
    },
    components: {
        Card,
    },
}
</script>

<style scoped lang="scss">
.row {
    width: 100%;
    padding: 0 25px;
    display: flex;
}
</style>
