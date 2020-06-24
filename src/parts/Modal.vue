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
                                    <img src="../assets/Dots.svg" />
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
                            <div class="historyDet">
                                <HistoryElem
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
                                                    src="../assets/Ellipse.svg"
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
                                            <img src="../assets/Ellipse.svg" />
                                        </div>
                                        <p class="task">
                                            {{ el.section.task }}
                                        </p>
                                    </div>
                                </HistoryElem>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
import HistoryElem from "../components/HistoryElem"

export default {
    name: "Modal",
    props: ["showModal", "info"],
    components: {
        HistoryElem,
    },
    methods: {
        closeModal() {
            this.$emit("toggleModal", false)
        },
        getIcon(path) {
            return require(`../assets/${path}`)
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
.footer {
    > span {
        font-family: monospace;
        font-style: normal;
        font-weight: 500;
        font-size: 12px;
        line-height: 12px;
        display: flex;
        align-items: center;
        color: #7d8790;
    }
}
.replay {
    > .task {
        font-family: monospace;
        margin: 5px 0 13px;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 16px;
        color: #35383d;
    }
    > .heading {
        > div {
            > span {
                font-weight: 500;
                margin-right: 7px;
            }
        }
        > span {
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            font-size: 12px;
            line-height: 12px;
            color: #35383d;
        }
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    > .footer {
        .action {
            margin-left: 2px;
        }
        margin-top: 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        > div {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
    }
    overflow: hidden;
    position: relative;
}
.leftHighlight {
    position: absolute;
    top: 11px;
    border: 2px solid;
    left: -2px;
    height: 33px;
    border-radius: 2px;
}
.social {
    .task {
        font-family: monospace;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 16px;
        color: #35383d;
    }
}
.slot {
    > .heading {
        span.social {
            font-feature-settings: "liga" off;
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            font-size: 12px;
            line-height: 12px;
        }
        span.name {
            color: #35383d;
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            font-size: 12px;
            line-height: 12px;
        }
        .right {
            > img {
                margin: 0 2px 0 5px;
            }
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        margin-bottom: 5px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    background: #ffffff;
    border: 2px solid #e9edf2;
}
.historyDet {
    display: flex;
    flex-direction: column-reverse;
}
.createMessage {
    margin: 10px 0 15px;
    padding: 10px;
    background: #ffffff;
    border: 2px solid #e9edf2;
    border-radius: 5px;
    > textarea {
        &::placeholder {
            color: #7d8790;
            opacity: 0.5;
        }
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
    > .actions {
        .pin {
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            margin: 0 4.36px 0 2.92px;
            color: #f2994a;
            font-size: 12px;
            line-height: 12px;
            font-feature-settings: "liga" off;
        }
        .cancel {
            font-family: monospace;
            margin-right: 10px;
            font-style: normal;
            font-weight: 500;
            font-size: 12px;
            line-height: 12px;
            color: #7d8790;
        }
        > span {
            font-feature-settings: "liga" off;
            color: #7d8790;
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            font-size: 12px;
            line-height: 12px;
        }
        display: flex;
        justify-content: space-between;
        align-items: center;
        > div {
            display: flex;
            justify-content: space-between;
            align-items: center;
            align-items: flex-end;
        }
    }
}
.history {
    > .title {
        > span {
            font-family: monospace;
            font-style: normal;
            font-weight: 500;
            font-size: 13px;
            line-height: 15px;
            text-align: right;
            color: #7d8790;
        }
        > div {
            > .historyTxt {
                margin: 0 7px;
                + {
                    img {
                        margin: 0 7px 0 4px;
                    }
                }
            }
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        margin-bottom: 6px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    padding: 13px 20px 6px;
}
.actions {
    > div {
        &:hover {
            cursor: pointer;
            box-shadow: 0 0 5px black;
        }
    }
}
.projectEdit {
    margin-top: 11px;
    background: #f3f6f8;
    border-radius: 3px;
    font-family: monospace;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    color: #7d8790;
    padding: 3px 6.02px 2px 5.26px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 6px;
}
.contactDet {
    margin-top: 8px;
    > .detail {
        > .value {
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 230px;
            font-weight: 500;
            color: #35383d;
        }
        > .key {
            font-weight: normal;
            color: #7d8790;
            width: 140px;
        }
        font-family: monospace;
        font-style: normal;
        margin: 8px 0;
        font-size: 14px;
        line-height: 17px;
        display: flex;
        justify-content: space-between;
    }
}
.project {
    > .contactDet {
        > .detail {
            > .value {
                color: #7d8790;
            }
        }
    }
    > p {
        margin-bottom: 8px;
        font-family: monospace;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 17px;
        color: #7d8790;
    }
}
.contacts {
    margin-bottom: 18px;
    > p {
        margin-bottom: 8px;
        font-family: monospace;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 17px;
        color: #7d8790;
    }
}
.about {
    .dots {
        background-color: #398bff1a;
        width: 40px;
        height: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 5px;
    }
    .action {
        background: #398bff1a;
        flex: auto;
        margin-left: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 5px;
        font-family: monospace;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #398bff;
    }
    > .actions {
        display: flex;
        margin: 15px 0 18px;
    }
    > .tags {
        > .tag {
            border: 1px solid #e9edf2;
            border-radius: 3px;
            padding: 1px 7px 1px 4px;
            margin-right: 8px;
        }
        margin-bottom: 15px;
        display: flex;
        font-family: monospace;
        color: #7d8790;
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 17px;
    }
    > .title {
        margin: 4px 0px 10px;
        font-family: monospace;
        font-style: normal;
        font-weight: 500;
        font-size: 18px;
        line-height: 21px;
        color: #35383d;
    }
    > .top {
        display: flex;
        justify-content: space-between;
        font-family: monospace;
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 14px;
        color: #7d8790;
    }
    padding: 10px 20px 13px;
    background-color: white;
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
.modalInner {
    width: 436.8px;
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
    display: flex;
    flex-direction: row-reverse;
}
.modal {
    top: 0;
    width: 100%;
    height: 100vh;
    position: fixed;
    flex-direction: row;
}
.slide-enter-active {
    transition: all 0.3s ease-out;
}
.slide-leave-active {
    transition: all 0.3s ease-in;
}
.slide-enter {
    transform: translateX(420px);
}
.slide-leave-to {
    transform: translateX(420px);
}
</style>
