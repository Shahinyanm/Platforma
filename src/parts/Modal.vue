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
                            <div class="title">{{ info.title }}</div>
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
                                    <img src="../assets/svg/Dots.svg" />
                                </div>
                                <div class="action">{{ info.action }}</div>
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
                                        <div class="value">{{ detail[1] }}</div>
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
                                                src="../assets/svg/arrDown.svg"
                                            />
                                        </div>
                                    </div>
                                </div>
                                <div class="projectEdit">
                                    <span>Проект</span>
                                    <img src="../assets/svg/pen.svg" />
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
                                                src="../assets/svg/arrDown.svg"
                                            />
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="history">
                            <div class="title">
                                <div>
                                    <img src="../assets/svg/bullHistory.svg" />
                                    <span class="historyTxt">История</span>
                                    <img src="../assets/svg/expand-list.svg" />
                                    <img src="../assets/svg/compact-list.svg" />
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
                                        <img src="../assets/svg/edit.svg" />
                                        <span class="pin">Заметка</span>
                                        <img src="../assets/svg/arrDown.svg" />
                                    </div>
                                    <span>Отправить</span>
                                </div>
                            </div>
                            <div class="historyDet">
                                <HistoryElement
                                    v-for="(el, index) in info.history"
                                    :key="index"
                                    :label="el.label"
                                    :time="el.time"
                                >
                                    <div
                                        class="slot replay"
                                        v-if="el.type === 'Replay'"
                                    >
                                        <div
                                            class="leftHighlight"
                                            :style="{
                                                borderColor:
                                                    el.section.actionColor,
                                            }"
                                        ></div>
                                        <div class="heading">
                                            <span>{{ el.section.name }}</span>
                                            <div>
                                                <span>{{
                                                    el.section.time
                                                }}</span>
                                                <img
                                                    src="../assets/svg/Ellipse.svg"
                                                />
                                            </div>
                                        </div>
                                        <p class="task">
                                            {{ el.section.task }}
                                        </p>
                                        <div class="hr1"></div>
                                        <div class="footer">
                                            <span>{{ el.section.date }}</span>
                                            <div>
                                                <img
                                                    :src="
                                                        getIcon(
                                                            el.section
                                                                .actionIcon
                                                        )
                                                    "
                                                />
                                                <span
                                                    class="action"
                                                    :style="{
                                                        color:
                                                            el.section
                                                                .actionColor,
                                                    }"
                                                    >{{
                                                        el.section.actionName
                                                    }}</span
                                                >
                                            </div>
                                        </div>
                                    </div>

                                    <div
                                        class="slot social"
                                        v-else-if="el.type === 'Social'"
                                    >
                                        <div class="heading">
                                            <div class="right">
                                                <span class="name">{{
                                                    el.section.name
                                                }}</span>
                                                <img
                                                    :src="
                                                        getIcon(
                                                            el.section
                                                                .actionIcon
                                                        )
                                                    "
                                                />
                                                <span
                                                    class="social"
                                                    :style="{
                                                        color:
                                                            el.section
                                                                .actionColor,
                                                    }"
                                                    >{{
                                                        el.section.actionName
                                                    }}</span
                                                >
                                            </div>
                                            <img
                                                src="../assets/svg/Ellipse.svg"
                                            />
                                        </div>
                                        <p class="task">
                                            {{ el.section.task }}
                                        </p>
                                    </div>
                                </HistoryElement>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
import HistoryElement from "../components/HistoryElement"

export default {
    name: "Modal",
    props: {
        showModal: {
            type: Boolean,
            required: true,
        },
        info: {
            type: Object,
            required: true,
        },
    },
    components: {
        HistoryElement,
    },
    methods: {
        closeModal() {
            this.$emit("toggleModal", false)
        },
        getIcon(path) {
            return require(`../assets/svg/${path}`)
        },
    },
    watch: {
        showModal(newVal) {
            document.body.style.overflow = newVal ? "hidden" : "auto"
        },
    },
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/parts/modal.scss";
</style>
