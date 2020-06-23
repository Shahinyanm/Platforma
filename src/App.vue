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
                <Column
                    v-for="(col, index) in Dummy.cols"
                    :col="col"
                    :key="index"
                />
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

export default {
    name: "App",
    data: () => ({
        Dummy,
        showModal: true,
    }),
    methods: {
        toggleModal(to) {
            if (to == this.showModal && to) {
                this.showModal = false
                return
                // console.log("asd")
            }
            this.showModal = to
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

<style>
* {
    margin: 0;
    padding: 0;
}
body {
    background-color: #f3f6f8;
}
.wrapper {
    position: relative;
}
.con {
    margin-top: 20px;
    padding: 0 50px;
}
#app {
    overflow-x: auto;
    height: 100vh;
}
.todo {
    padding: 0 20px;
    margin-top: 18px;
    display: flex;
}
</style>
