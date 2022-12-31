<template>
    <div>
        <el-card class="box-card">
            <div slot="header">
                <el-button @click="fresh">控制子组件</el-button>
            </div>
            <parent-control ref="child" :refresh="refresh" :user="user"/>
        </el-card>
    </div>
</template>
<script>
import {EventBus, EventType} from './util/EventBus'
import {MittBus, MittType} from './util/MittEvent'
import ParentControl from './util/ParentControl.vue'
export default {
    name: 'MainComp',
    components: {
        ParentControl
    },
    provide: function() {
        // 传递对象
        return {
            text: this.msg
        }
    },
    data: function() {
        return {
            refresh: false,
            msg: {
                text: '哈哈哈'
            },
            user: {
            },
        }
    },
    methods: {
        fresh() {
            // 方法三
            EventBus.$emit(EventType.DATA_TYPE, '童叟无欺')
            MittBus.emit(MittType.DATA_TYPE, 'mitt童叟无欺')
            // 方法二
            // this.$refs.child.addOne()
            // console.log(this.$refs)
            // console.log(this.$refs.child.addOne())
            // 方法一
            // this.refresh = !this.refresh;
        }
    },
    mounted() {
        setTimeout(() => {
            // 变更对象的值
            this.msg.text = '哈哈哈，我变了'
            console.log(this.msg, this.injectVal)

            // 异步加载
            // 受 ES5 的限制，Vue.js 不能检测到对象属性的添加或删除。
            this.$set(this.user, 'info', {name: '大象'})
        }, 5000)
    }
}
</script>