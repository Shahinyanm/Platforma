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
        <Loading v-if="loading" />
    </div>
</template>

<script>
import Header from "./parts/Header.vue"
import TopRow from "./parts/TopRow.vue"
import Column from "./parts/Column.vue"
import Modal from "./parts/Modal.vue"
import Dummy from "./Dummy.json"
import Loading from "./parts/Loading"

export default {
    name: "App",
    data: () => ({
        Dummy: Dummy,
        cols: [],
        dataDelta: 10,
        maxHistorySize: 0,
        currentHistorySize: 0,
        showModal: false,
        loading: true,
    }),
    components: {
        Modal,
        Column,
        TopRow,
        Header,
        Loading,
    },
    created() {
        window.addEventListener("scroll", this.scrollListener)
    },
    mounted() {
        setTimeout(() => {
            console.log(this.dum)
        }, 2000)
        this.updateCols().then(() => (this.loading = false))
    },
    methods: {
        updateCols() {
            this.maxHistorySize = Math.max(
                ...this.Dummy.cols.map((el) => el.cards.length)
            )
            return new Promise((resolve) => {
                setTimeout(() => {
                    this.cols = this.Dummy.cols.map((col) =>
                        Object.assign(
                            { ...col },
                            {
                                cards: col.cards.slice(
                                    0,
                                    this.currentHistorySize + this.dataDelta
                                ),
                            }
                        )
                    )
                    this.currentHistorySize += this.dataDelta
                    resolve()
                }, 2000)
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
                document.body.scrollHeight + 70
            if (
                isBottomHit &&
                this.currentHistorySize < this.maxHistorySize &&
                !this.loading
            ) {
                this.loading = true
                this.updateCols().then(() => (this.loading = false))
            }
        },
    },
    watch: {
        loading(newLoad) {
            if (newLoad) {
                document.body.style.overflow = "hidden"
            } else {
                document.body.style.overflow = "auto"
            }
        },
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
