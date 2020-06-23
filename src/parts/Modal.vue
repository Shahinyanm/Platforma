<template>
    <transition name="slide">
        <div class="modal" v-show="showModal">
            <div class="headerTransparent"></div>
            <div>
                <div class="modalOuter" @click.self="closeModal">
                    <div class="modalInner">
                        <div class="about">
                            <div class="top">
                                <span>{{ info.number }}</span>
                                <span>{{ info.time }}</span>
                            </div>
                            <div class="title">
                                {{ info.title }}
                            </div>
                            <div class="tags">
                                <div
                                    v-for="(tag, index) in info.tags"
                                    :key="index"
                                    class="tag"
                                >
                                    {{ tag }}
                                </div>
                            </div>
                            <div class="hr"></div>
                            <div class="actions">
                                <div class="dots">
                                    <img src="../assets/Dots.svg" />
                                </div>
                                <div class="action">
                                    {{ info.action }}
                                </div>
                            </div>
                            <div class="contacts">
                                <p>Контакты</p>
                                <div class="hr"></div>
                                <div class="contactDet">
                                    <div
                                        v-for="(detail, index) in info.contacts"
                                        :key="index"
                                        class="detail"
                                    >
                                        <div class="key">{{ detail[0] }}</div>
                                        <div class="value">
                                            {{ detail[1] }}
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="project">
                                <p>Проект</p>
                                <div class="hr"></div>
                                <div class="contactDet">
                                    <div
                                        v-for="(detail, index) in info.project
                                            .part1"
                                        :key="index"
                                        class="detail"
                                    >
                                        <div class="key">{{ detail[0] }}</div>
                                        <div class="value">
                                            {{ detail[1] }}
                                            <img
                                                v-if="index === 0"
                                                src="../assets/arrDown.svg"
                                            />
                                        </div>
                                    </div>
                                </div>
                                <div class="projectEdit">
                                    <span>Проект</span>
                                    <img src="../assets/pen.svg" />
                                </div>
                                <div class="hr"></div>
                                <div class="contactDet">
                                    <div
                                        v-for="(detail, index) in info.project
                                            .part2"
                                        :key="index"
                                        class="detail"
                                    >
                                        <div class="key">{{ detail[0] }}</div>
                                        <div class="value">
                                            {{ detail[1] }}
                                            <img
                                                v-if="index === 0"
                                                src="../assets/arrDown.svg"
                                            />
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="history">
                            <div class="title">
                                <div>
                                    <img src="../assets/bullHistory.svg" />
                                    <span class="historyTxt">История</span>
                                    <img src="../assets/expand-list.svg" />
                                    <img src="../assets/compact-list.svg" />
                                </div>
                                <span>{{ info.history.length }}</span>
                            </div>
                            <div class="hr"></div>
                            <div class="createMessage">
                                <textarea
                                    placeholder="Напишите текст Заметки или Сообщения..."
                                ></textarea>
                                <div class="hr1"></div>
                                <div class="actions">
                                    <div>
                                        <span class="cancel">Отменить</span>
                                        <img src="../assets/edit.svg" />
                                        <span class="pin">Заметка</span>
                                        <img src="../assets/arrDown.svg" />
                                    </div>
                                    <span>Отправить</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    name: "Modal",
    props: ["showModal", "info"],
    methods: {
        closeModal() {
            this.$emit("toggleModal", false)
        },
    },
    watch: {
        showModal(newVal) {
            document.getElementById("app").style.overflow = newVal
                ? "hidden"
                : "auto"
        },
    },
}
</script>

<style scoped>
.createMessage {
    margin-top: 10px;
    padding: 10px;
    background: #ffffff;
    /* Light Gray */

    border: 2px solid #e9edf2;
    border-radius: 5px;
}
.createMessage > textarea::placeholder {
    color: #7d8790;
    opacity: 0.5;
}

.createMessage > textarea {
    width: 100%;
    resize: none;
    height: 16px;
    border: none;
    outline: none;
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 16px;
}
.history > .title > span {
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 13px;
    line-height: 15px;
    /* identical to box height */

    text-align: right;

    /* Gray */

    color: #7d8790;
}
.createMessage > .actions .pin {
    font-family: TT Norms;
    font-style: normal;
    font-weight: 500;
    margin: 0 4.36px 0 2.92px;
    color: #f2994a;
    font-size: 12px;
    line-height: 12px;
    /* identical to box height, or 100% */

    font-feature-settings: "liga" off;
}
.createMessage > .actions .cancel {
    font-family: monospace;
    margin-right: 10px;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 12px;
    /* identical to box height, or 100% */

    /* Gray */

    color: #7d8790;
}
.history > .title > div > .historyTxt {
    margin: 0 7px;
}
.history > .title > div > .historyTxt + img {
    margin: 0 7px 0 4px;
}
.history > .title {
    margin-bottom: 6px;
}
.createMessage > .actions > span {
    font-feature-settings: "liga" off;

    /* Gray */

    color: #7d8790;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 12px;
}

.history > .title,
.history > .title > div,
.createMessage > .actions,
.createMessage > .actions > div {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.createMessage > .actions > div {
    align-items: flex-end;
}
.history {
    padding: 13px 20px 13px;
}

/*//////////////////////////////about///////////////////////////////////////*/

.projectEdit {
    margin-top: 11px;
    background: #f3f6f8;
    border-radius: 3px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    /* identical to box height */

    /* Gray */

    color: #7d8790;
    padding: 3px 6.02px 2px 5.26px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 6px;
}
.contactDet {
    margin-top: 8px;
}

.project > .contactDet > .detail > .value {
    color: #7d8790;
}
.contactDet > .detail > .value {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 230px;
    font-weight: 500;
    color: #35383d;
}
.contactDet > .detail > .key {
    font-weight: normal;
    color: #7d8790;
    width: 140px;
    /* margin-right: 10px; */
}
.contactDet > .detail {
    font-family: monospace;
    font-style: normal;
    margin: 8px 0;
    font-size: 14px;
    line-height: 17px;
    /* identical to box height */

    /* Gray */

    display: flex;
    justify-content: space-between;
}
.contacts {
    margin-bottom: 18px;
}
.contacts > p,
.project > p {
    margin-bottom: 8px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    /* identical to box height */

    /* Gray */

    color: #7d8790;
}
.about .dots {
    background-color: #398bff1a;
    /* opacity: 0.1; */
    width: 40px;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
}
.about .action {
    background: #398bff1a;
    flex: auto;
    margin-left: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* opacity: 0.1; */
    border-radius: 5px;

    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    /* identical to box height */

    text-align: center;

    /* Blue (Logo) */

    color: #398bff;
}
.about > .actions {
    display: flex;
    margin: 15px 0 18px;
}
.hr {
    height: 0;
    border-radius: 2px;
    border: 2px solid #e9edf2;
}
.hr1 {
    height: 0;
    margin: 10px 0;

    border-top: 1px solid #e9edf2;
}
.about > .tags > .tag {
    border: 1px solid #e9edf2;
    border-radius: 3px;
    padding: 1px 7px 1px 4px;
    margin-right: 8px;
}
.about > .tags {
    margin-bottom: 15px;
    display: flex;
    font-family: monospace;
    color: #7d8790;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
}
.about > .title {
    margin: 4px 0px 10px;

    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 18px;
    line-height: 21px;

    /* Text */

    color: #35383d;
}
.about > .top {
    display: flex;
    justify-content: space-between;
    font-family: monospace;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 14px;

    /* Gray */

    color: #7d8790;
}
.about {
    padding: 10px 20px 13px;
    background-color: white;
}
.modalInner {
    width: 428.4px;
    background-color: #f3f6f8;
    height: calc(100vh - 50px);
    overflow-y: auto;
    box-shadow: 0px 10px 55px rgba(52, 61, 86, 0.25),
        0px 5px 25px rgba(52, 61, 86, 0.15);
}
.headerTransparent {
    height: 50px;
    width: 100%;
}
.modalOuter {
    /* background-color: #000000a0; */
    display: flex;
    flex-direction: row-reverse;
}
.modal {
    top: 0;
    width: 100%;
    height: 100vh;
    /* background-color: #000000a0; */
    position: fixed;
    /* display: flex; */
    flex-direction: row;
}
.slide-enter-active {
    transition: all 0.3s ease-out;
}
.slide-leave-active {
    transition: all 0.3s ease-in;
}
.slide-enter,
.slide-leave-to {
    transform: translateX(420px);
}
</style>
