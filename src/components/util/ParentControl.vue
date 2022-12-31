<template>
    <div ref="nb">受控数字：{{ number }}, 子组件绑定了注入的字符串{{ text.text }}
        <div v-if="!showName" v-loading="!showName"></div>
        <div v-else>用户名：{{ user.info.name }}</div>
    </div>
</template>
<script>
import { EventBus, EventType } from './EventBus'
import { MittBus, MittType } from './MittEvent'
export default {
    name: "ParentControl",
    props: ['refresh', 'user'],
    inject: ['text'],
    data: function () {
        return {
            number: 0,
            showName: false,
        }
    },
    watch: {
        refresh: function () {
            this.addOne()
        },
        user: {
            handler: function (newValue) {
                console.log('我被执行了')
                if (newValue?.info?.name) {
                    this.showName = true;
                }
            },
            deep: true
        }
    },
    methods: {
        addOne() {
            this.number = this.number + 1;
        }
    },
    mounted() {
        // EventBus.$on(EventType.DATA_TYPE, (msg) => {
        //     console.log(msg)
        //     this.addOne()
        // })
        MittBus.on(MittType.DATA_TYPE, (msg) => {
            console.log(msg)
            this.addOne()
        })
        console.log('this.injectVal', this.injectVal)
    }
}
</script>