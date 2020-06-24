<template>
    <div id="app">
        <Header @toggleModal="toggleModal" />
        <div class="wrapper">
            <Modal
                :showModal="showModal"
                @toggleModal="toggleModal"
                :info="Dummy.modalData"
            />
        </div>
        <div class="con">
            <TopRow :topRow="Dummy.topRow" />
            <div class="todo">
                <Column v-for="(col, index) in cols" :col="col" :key="index" />
            </div>
        </div>
    </div>
</template>

<script>
import Header from "./parts/Header.vue"
import TopRow from "./parts/TopRow.vue"
import Column from "./parts/Column.vue"
import Modal from "./parts/Modal.vue"
import Dummy from "./Dummy"
console.log(Dummy.cols)
export default {
    name: "App",
    created() {
        window.addEventListener("scroll", this.scrollListener)
    },
    mounted() {
        this.updateCols()
    },
    data: () => ({
        Dummy,
        cols: [],
        dataDelta: 10,
        currentHistorySize: 0,
        showModal: false,
        loading: false,
    }),
    methods: {
        updateCols() {
            return new Promise((resolve) => {
                setTimeout(() => {
                    this.cols = this.Dummy.cols.map((col) =>
                        Object.assign(col, {
                            cards: col.cards.slice(
                                0,
                                this.currentHistorySize + this.dataDelta
                            ),
                        })
                    )
                    this.currentHistorySize += this.dataDelta
                    resolve()
                }, 3000)
            })
        },
        toggleModal(to) {
            if (to == this.showModal && to) {
                this.showModal = false
                return
            }
            this.showModal = to
        },
        scrollListener() {
            let isBottomHit =
                window.scrollY + window.innerHeight >=
                document.body.scrollHeight

            let maxLength = 0
            this.Dummy.cols.forEach((col) => {
                if (maxLength < col.cards.length) maxLength = col.cards.length
                console.log(col.cards.length)
            })
            console.log(maxLength)
            if (isBottomHit && this.currentHistorySize < maxLength) {
                this.loading = true
                this.updateCols().then(() => {
                    console.log("asdasd")
                    this.loading = false
                })
            }
        },
    },
    components: {
        Modal,
        Column,
        TopRow,
        Header,
    },
}
</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
}
body {
    overflow-x: auto;
    background-color: #f3f6f8;
}
.wrapper {
    position: relative;
}
.con {
    margin-top: 70px;
    padding: 0 50px;
}
.todo {
    padding: 0 20px;
    margin-top: 18px;
    display: flex;
}
</style>
