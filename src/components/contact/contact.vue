<template lang="pug">
    .contact
        search
        .group
            tab-cell(img="", :title="titles[0]", contact)
            tab-cell(img="", :title="titles[1]", contact)
            tab-cell(img="", :title="titles[2]", contact)
            tab-cell(img="", :title="titles[3]", contact)
        .group
            tab-cell(img="", :title="titles[4]", contact)
            tab-cell(img="", :title="titles[5]", contact)
        .group
            tab-cell(img="", :title="titles[6]", contact)
            tab-cell(img="", :title="titles[7]", contact)
            tab-cell(img="", :title="titles[8]", contact)
        .group
            tab-cell(img="", :title="titles[9]", contact)
        .group
            tab-cell(img="", :title="titles[10]", contact)
            tab-cell(img="", :title="titles[11]", contact)
</template>

<script>
import TabCell from '@/components/common/tab-cell'
import Search from '@/components/common/search'

export default {
    data () {
        return {
            titles: ['新的朋友', '群聊', '标签', '公众号',
                    '张三', '小明', '小黄', '小黑',
                    '阿兰', '明月心', '黄蓉', '郭靖']
        }
    },
    components: {
        TabCell,
        Search
    }
}
</script>

<style lang="scss" scoped>
.contact {
    // position: relative;
    .group {
        margin: 18px 0 4px;

        border-top: 1px solid #ccc;
        border-bottom: 1px solid #ccc;
    }
    .group:nth-child(2) {
        margin-top: 0;
    }
}
</style>
