<template lang="pug">
    li.message-list
        header.header
            img
        section.content
            .top
                span.title {{ name }}
                span.time {{ time }}
            .bottom
                p.context {{ text }}
                i.icon(v-if="disturb")
</template>

<script>
export default {
    props: ['index'],
    computed: {
        disturb () {
            return false
        },
        name () {
            // 聊天列表的名字
            return this.$store.state.chatLog[this.index].name
        },
        time () {
            // 最后一条消息 时间
            const messages = this.$store.state.chatLog[this.index].messages
            const last = messages.length
            return messages[last - 1].time
        },
        text () {
            // 最后一条消息 内容
            const messages = this.$store.state.chatLog[this.index].messages
            const last = messages.length
            return messages[last - 1].text
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/mixin';

.message-list {
    position: relative;
    height: 68px;
    padding: 0 12px;

    background-color: #fff;
    @include flex(space-start)

    .header {
        margin-right: 8px;

        img {
            width: 48px;
            height: 48px;
        }
    }
    .content {
        height: 48px;
        // 将父容器撑满
        width: 100%;

        @include flex(space-around, flex-start, column)

        .top {
            width: 100%;
            @include flex(space-between)

            .title {
                font-size: 15px;
                font-weight: bold;
            }
            .time {
                font-size: 70%;
                color: #999;
            }
        }
        .bottom {
            width: 100%;

            @include flex(space-between)

            .context {
                // 限制死了最大宽度, 防止内容超出父容器
                // max-width: 230px;
                font-size: 75%;
                color: #666;

                white-space: nowrap;
                text-overflow: ellipsis;
                overflow: hidden;
            }

            // 暂时 通过响应式解决
            @media screen and (min-width: 320px) and (max-width: 375px) {
                .context {
                    max-width: 230px;
                }
            }
            @media screen and (min-width: 375px) and (max-width: 414px) {
                .context {
                    max-width: 280px;
                }
            }
            @media screen and (min-width: 414px) {
                .context {
                    max-width: 80%;
                }
            }

            .icon {
                display: inline-block;
                width: 10px;
                height: 10px;

                background-color: #98ea12;
            }
        }

    }

    // 下划线 除了最后一个
    &:not(:nth-last-of-type(1))::after {
        content: '';
        @include abs(auto, 0, 0, 12px)
        height: 1px;

        background-color: #ccc;
    }
    // 点击变暗效果
    &:active {
        background-color: #d9d9d9;
    }
}
</style>
